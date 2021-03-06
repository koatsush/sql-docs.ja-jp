---
title: catalog.executable_statistics | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c96ea5b857bb95477e34464cb84b870b21d993e6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017455"
---
# <a name="catalogexecutablestatistics"></a>catalog.executable_statistics 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  実行される各実行可能ファイル (実行可能ファイルの各繰り返しを含む) に対する行を表示します。  
  
 実行可能ファイルは、パッケージの制御フローに追加するタスクまたはコンテナーです。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|Statistics_id|BIGINT|データの一意の ID。|  
|Execution_id|BIGINT|実行のインスタンスの一意の ID。<br /><br /> catalog.executions ビューには、実行に関する追加情報が表示されます。 詳細については、「[catalog.executions &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)」を参照してください。|  
|Executable_id|BIGINT|パッケージ コンポーネントの一意の ID。<br /><br /> catalog.executables ビューには、実行可能ファイルに関する追加情報が表示されます。 詳細については、「[catalog.executables](../../integration-services/system-views/catalog-executables.md)」を参照してください。|  
|Execution_path|nvarchar(max)|コンポーネントの各繰り返しを含む、パッケージ コンポーネントの実行の完全パス。|  
|Start_time|datetimeoffset(7)|実行可能ファイルが実行前フェーズに入ったときの時刻。|  
|End_time|datetimeoffset(7)|実行可能ファイルが実行後フェーズに入ったときの時刻。|  
|Execution_duration|INT|実行可能ファイルの実行に費やされた時間の長さ。 値の単位はミリ秒です。|  
|Execution_result|SMALLINT|使用できる値を次に示します。<br /><br /> 0 (成功)<br /><br /> 1 (失敗)<br /><br /> 2 (完了)<br /><br /> 3 (キャンセル)|  
|Execution_value|sql_variant|実行によって返される値。 これは、ユーザー定義の値です。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスに対する READ 権限。  
  
-   **ssis_admin** データベース ロールのメンバーシップ。  
  
-   **sysadmin** サーバー ロールのメンバーシップ。  
  
  
