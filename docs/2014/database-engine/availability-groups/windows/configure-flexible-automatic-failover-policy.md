---
title: 条件を制御する (Always On 可用性グループ) の自動フェールオーバーの柔軟なフェールオーバー ポリシーの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b9a063413a665d9e159cb513ea936ab851715ce4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62815259"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a>自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)
  このトピックでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]または PowerShell を使用して AlwaysOn 可用性グループの柔軟なフェールオーバー ポリシーを構成する方法について説明します。 柔軟なフェールオーバー ポリシーを使用すると、可用性グループの自動フェールオーバーを実行する条件をきめ細かく制御できます。 自動フェールオーバーを実行するエラー条件および正常性チェックの頻度を変更することで、自動フェールオーバーの確率値を増減して高可用性の SLA をサポートできます。  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Limitations"></a> 自動フェールオーバーの制限  
  
-   自動フェールオーバーが行われるには、現在のプライマリ レプリカおよび 1 つのセカンダリ レプリカが自動フェールオーバーを使用する同期コミット可用性モード用に構成され、セカンダリ レプリカがプライマリ レプリカと同期している必要があります。  
  
-   WSFC クラスターでは、可用性グループが WSFC のエラーしきい値を超えると、自動フェールオーバーはその可用性グループに対して実行されません。 また、クラスター管理者が失敗したリソース グループを手動でオンラインにするか、データベース管理者が可用性グループの手動フェールオーバーを実行するまで、可用性グループの WSFC リソース グループはエラー状態のままになります。 *WSFC のエラーしきい値* は、特定の期間に可用性グループに対して許容されるエラーの最大数として定義されています。 既定の期間は 6 時間であり、この期間のエラーの最大数の既定値は *n*-1 です ( *n* は WSFC ノードの数です)。 特定の可用性グループのエラーしきい値を変更するには、WSFC フェールオーバー マネージャー コンソールを使用します。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
  
|タスク|アクセス許可|  
|----------|-----------------|  
|新しい可用性グループの柔軟なフェールオーバー ポリシーを構成する|**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。|  
|既存の可用性グループのポリシーを変更する|可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。|  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **柔軟なフェールオーバー ポリシーを構成するには**  
  
1.  プライマリ レプリカをホストするサーバー インスタンスに接続します。  
  
2.  新しい可用性グループの場合は、 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。 既存の可用性グループを変更する場合は、 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。  
  
    -   フェールオーバーの条件レベルを設定するには、FAILURE_CONDITION_LEVEL = *n* オプションを使用します。ここで、 *n* は 1 ～ 5 の整数です。  
  
         たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、既存の可用性グループ `AG1`のエラー条件レベルをレベル 1 に変更します。  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         これらの整数値とエラー条件レベルの関係は次のとおりです。  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] の値|Level|自動フェールオーバーが開始される条件|  
        |------------------------------|-----------|-------------------------------------------|  
        |1|1|サーバーの停止。 フェールオーバーまたは再起動のため、SQL Server サービスが停止した場合。|  
        |2|2|サーバーの応答停止。 下限値の任意の条件が満たされた場合、SQL Server サービスがクラスターに接続され正常性チェックのタイムアウトしきい値を超えた場合、または現在のプライマリ レプリカがエラー状態になった場合。|  
        |3|3|重大なサーバー エラー。 下限値の任意の条件が満たされるか、重大な内部サーバー エラーが発生した場合。<br /><br /> これは既定のレベルです。|  
        |4|4|中程度のサーバー エラー。 下限値の任意の条件が満たされるか、中程度のサーバー エラーが発生した場合。|  
        |5|5|任意の限定されたエラー条件。 下限値の任意の条件が満たされるか、限定されたエラー条件が発生した場合。|  
  
         詳細については、「[可用性グループの自動フェールオーバーのための柔軟なフェールオーバー ポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)」を参照してください。  
  
    -   正常性チェックのタイムアウトしきい値を構成するには、HEALTH_CHECK_TIMEOUT = *n* オプションを使用します。ここで *n* は 15000 ミリ秒 (15 秒) ～ 4294967295 ミリ秒の整数です。 既定値は 30000 ミリ秒 (30 秒) です。  
  
         たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、既存の可用性グループ `AG1`の正常性チェックのタイムアウトしきい値が  60,000 ミリ秒 (1 分) に変更されます。  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
 **柔軟なフェールオーバー ポリシーを構成するには**  
  
1.  既定 (`cd`) を、プライマリ レプリカをホストするサーバー インスタンスに設定します。  
  
2.  可用性グループに可用性レプリカを追加する場合は、`New-SqlAvailabilityGroup` コマンドレットを使用します。 既存の可用性レプリカを変更する場合は、`Set-SqlAvailabilityGroup` コマンドレットを使用します。  
  
    -   フェールオーバー条件レベルを設定するには使用、 `FailureConditionLevel`*レベル*パラメーター、どこで、*レベル*は、次の値の 1 つです。  
  
        |値|Level|自動フェールオーバーが開始される条件|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|1|サーバーの停止。 フェールオーバーまたは再起動のため、SQL Server サービスが停止した場合。|  
        |`OnServerUnresponsive`|2|サーバーの応答停止。 下限値の任意の条件が満たされた場合、SQL Server サービスがクラスターに接続され正常性チェックのタイムアウトしきい値を超えた場合、または現在のプライマリ レプリカがエラー状態になった場合。|  
        |`OnCriticalServerError`|3|重大なサーバー エラー。 下限値の任意の条件が満たされるか、重大な内部サーバー エラーが発生した場合。<br /><br /> これは既定のレベルです。|  
        |`OnModerateServerError`|4|中程度のサーバー エラー。 下限値の任意の条件が満たされるか、中程度のサーバー エラーが発生した場合。|  
        |`OnAnyQualifiedFailureConditions`|5|任意の限定されたエラー条件。 下限値の任意の条件が満たされるか、限定されたエラー条件が発生した場合。|  
  
         詳細については、「[可用性グループの自動フェールオーバーのための柔軟なフェールオーバー ポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)」を参照してください。  
  
         たとえば、次のコマンドでは、既存の可用性グループ `AG1`のエラー条件レベルをレベル 1 に変更します。  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `   
        -FailureConditionLevel OnServerDown  
        ```  
  
    -   正常性チェックのタイムアウトしきい値を設定するには、使用、 `HealthCheckTimeout` *n*パラメーター、どこで、 *n*は 15000 ミリ秒 (15 秒) ~ 4294967295 ミリ秒の整数。 既定値は 30000 ミリ秒 (30 秒) です。  
  
         たとえば、次のコマンドでは、既存の可用性グループ `AG1`の正常性チェックのタイムアウトしきい値が 120,000 ミリ秒 (2 分) に変更されます。  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
        -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)   
 [フェールオーバーとフェールオーバー モード&#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [フェールオーバー クラスター インスタンスのフェールオーバー ポリシー](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
  
  
