---
title: データベースを新しい場所に復元する (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bef38ae0b93eb43d508192c6f748a36320143689
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937538"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a>データベースを新しい場所に復元する (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、SQL Server Management Studio(SSMS) または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)]データベースを新しい場所に復元し、必要に応じてデータベースの名前を変更する方法について説明します。 新しいディレクトリ パスにデータベースを移動できるほか、同じサーバー インスタンスまたは別のサーバー インスタンスにデータベースのコピーを作成できます。  
    
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   データベースの完全バックアップの復元中は、復元作業を実行するシステム管理者以外は、復元中のデータベースを使用しないでください。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   完全復旧モデルまたは一括ログ復旧モデルを使用する場合は、データベースを復元する前に、アクティブ トランザクション ログをバックアップする必要があります。 詳細については、「 [トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)」を参照してください。  

-   暗号化されたデータベースを復元するには、 **データベースを暗号化するために使用した証明書や非対称キーにアクセスする必要があります**。 証明書または非対称キーがないと、データベースを復元することはできません。 バックアップが必要な間は、データベースの暗号化キーの暗号化に使用した証明書を保持する必要があります。 詳細については、「 [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   データベースの移行に関するその他の考慮事項については、「 [バックアップと復元によるデータベースのコピー](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)」を参照してください。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のデータベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]に復元すると、データベースが自動的にアップグレードされます。 通常、データベースは直ちに使用可能になります。 ただし、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、  **upgrade_option** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。 アップグレード オプションがインポート (**upgrade_option** = 2) または再構築 (**upgrade_option** = 0) に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。 インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。 また、アップグレード オプションがインポートに設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。 **upgrade_option** サーバー プロパティの設定を変更するには、 [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)を使用します。  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティを確保するため、不明なソースや信頼されていないソースからのデータベースは、アタッチまたは復元しないことをお勧めします。 こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。 不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。  
  
####  <a name="Permissions"></a> Permissions  
 復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。 データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています。  
  
 RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。 固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。  
  
  
## <a name="restore-a-database-to-a-new-location-optionally-rename-the-database-using-ssms"></a>新しい場所にデータベースを復元し、必要に応じて SSMS を使用してデータベースの名前を変更する 

  
1.  適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[データベース]** を右クリックし、 **[データベースの復元]** をクリックします。 **[データベースの復元]** ダイアログ ボックスが表示されます。  
  
3.  **[全般]** ページの **復元元**のセクションを使用して、復元するバックアップ セットの復元元ファイルと場所を指定します。 以下のオプションの 1 つを選択します。  
  
    -   **[データベース]**  
  
         復元するデータベースをドロップダウン リストから選択します。 このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。  
  
    > **注:** 別のサーバーで作成されたバックアップの場合、復元先のサーバーには指定されたデータベースのバックアップ履歴情報が存在しません。 この場合、 **[デバイス]** をクリックして、復元するファイルまたはデバイスを手動で指定します。  
  
    1.  **[デバイス]**  
  
         参照ボタン ( **[...]** ) をクリックし、 **[バックアップ デバイスの選択]** ダイアログ ボックスを開きます。 **[バックアップ メディアの種類]** ボックスから、デバイスの種類を 1 つ選択します。 **[バックアップ メディア]** ボックスにデバイスを追加するには、 **[追加]** をクリックします。  
  
         **[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。  
  
         **[ソース: デバイス: データベース]** リスト ボックスで、復元するデータベースの名前を選択します。  
  
         **メモ** この一覧は **[デバイス]** をクリックした場合にのみ使用できます。 選択されたデバイスにバックアップを持つデータベースのみが使用できるようになります。  
  
4.  **復元先のセクション**の **[データベース]** ボックスに、復元するデータベースの名前が自動的に表示されます。 データベースの名前を変更するには、 **[データベース]** ボックスに新しい名前を入力します。  
  
5.  **[復元先]** ボックスで、既定値の **[最後に作成されたバックアップ]** のままにするか、 **[タイムライン]** をクリックして、 **[バックアップのタイムライン]** ダイアログ ボックスにアクセスし、具体的にどの時点で復旧アクションを停止するかを手動で選択します。 特定の時点を指定する方法の詳細については、「 [Backup Timeline](../../relational-databases/backup-restore/backup-timeline.md) 」を参照してください。  
  
6.  **[復元するバックアップ セット]** グリッドで、復元するバックアップを選択します。 このグリッドには、指定された場所に対して使用可能なバックアップが表示されます。 既定では、復旧計画が推奨されています。 推奨された復元計画を変更するには、グリッドの選択を変更します。 以前のバックアップの選択を解除すると、以前のバックアップの復元に依存するバックアップは自動的に選択が解除されます。  
  
     **[復元するバックアップ セット]** グリッドの列の詳細については、「[データベースの復元 &#40;[全般] ページ&#41;](../../relational-databases/backup-restore/restore-database-general-page.md)」を参照してください。  
  
7.  データベース ファイルの新しい場所を指定するには、 **[ファイル]** ページを選択し、 **[すべてのファイルをフォルダーに移動する]** をクリックします。 **[データ ファイルのフォルダー]** および **[ログ ファイルのフォルダー]** の新しい場所を指定します。 このグリッドの詳細については、「[データベースの復元 &#40;[ファイル] ページ&#41;](../../relational-databases/backup-restore/restore-database-files-page.md)」を参照してください。  
  
8.  **[オプション]** ページで必要に応じてオプションを調整します。 これらのオプションの詳細については、「[データベースの復元 &#40;[オプション] ページ&#41;](../../relational-databases/backup-restore/restore-database-options-page.md)」を参照してください。  

 ## <a name="restore-database-to-a-new-location-optionally-rename-the-database-using-t-sql"></a>新しい場所にデータベースを復元し、必要に応じて T-SQL を使用してデータベースの名前を変更する
 
 
1.  必要に応じて、復元するデータベースの完全バックアップを含んでいるバックアップ セット内のファイルの論理名と物理名を判断します。 このステートメントは、バックアップ セットに保存されているデータベースとログ ファイルのリストを返します。 基本構文は次のとおりです。  
  
     RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number* 
  
     この *backup_set_file_number* は、メディア セット内のバックアップの位置を示します。 バックアップ セットの位置は、 [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) ステートメントを使用して取得できます。 詳細については、「[RESTORE の引数 &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)」の「バックアップ セットの指定」を参照してください。  
  
     このステートメントは、多くの WITH オプションもサポートします。 詳細については、[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md) を参照してください。  
  
2.  [RESTORE DATABASE](../../t-sql/statements/restore-statements-transact-sql.md) ステートメントを使用し、データベースの完全バックアップを復元します。 既定で、データとログ ファイルが元の場所に復元されます。 データベースを再配置するには、MOVE オプションを使用して、各データベース ファイルを再配置し、既存ファイルとの衝突が発生するのを防ぎます。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for restoring the database to a new location and a new name is:  
  
     RESTORE DATABASE *new_database_name*  
  
     FROM *backup_device* [ ,...*n* ]  
  
     [ WITH  
  
     {  
  
     [ **RECOVERY** | NORECOVERY ]  
  
     [ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]  
  
     [ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]  
  
     }  
  
     ;  
  
    > **NOTE!** When preparing to relocate a database on a different disk, you should verify that sufficient space is available and identify any potential collisions with existing files. This involves using a [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md) statement that specifies the same MOVE parameters that you plan to use in your RESTORE DATABASE statement.  
  
     The following table describes arguments of this RESTORE statement in terms of restoring a database to a new location. For more information about these arguments, see [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).  
  
     *new_database_name*  
     The new name for the database.  
  
    >**NOTE:** If you are restoring the database to a different server instance, you can use the original database name instead of a new name.  
  
     *backup_device* [ **,**...*n* ]  
     Specifies a comma-separated list of from 1 to 64 backup devices from which the database backup is to be restored. You can specify a physical backup device, or you can specify a corresponding logical backup device, if defined. To specify a physical backup device, use the DISK or TAPE option:  
  
     { DISK | TAPE } **=**_physical_backup_device_name_  
  
     For more information, see [Backup Devices &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
     { **RECOVERY** | NORECOVERY }  
     If the database uses the full recovery model, you might need to apply transaction log backups after you restore the database. In this case, specify the NORECOVERY option.  
  
     Otherwise, use the RECOVERY option, which is the default.  
  
     FILE = { *backup_set_file_number* | @*backup_set_file_number* }  
     Identifies the backup set to be restored. For example, a *backup_set_file_number* of **1** indicates the first backup set on the backup medium and a *backup_set_file_number* of **2** indicates the second backup set. You can obtain the *backup_set_file_number* of a backup set by using the [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) statement.  
  
     When this option is not specified, the default is to use the first backup set on the backup device.  
  
     For more information, see "Specifying a Backup Set," in [RESTORE Arguments &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
     MOVE **'**_logical_file_name_in_backup_**'** TO **'**_operating_system_file_name_**'** [ **,**...*n* ]  
     Specifies that the data or log file specified by *logical_file_name_in_backup* is to be restored to the location specified by *operating_system_file_name*. Specify a MOVE statement for every logical file you want to restore from the backup set to a new location.  
  
    |オプション|Description|  
    |------------|-----------------|  
    |*logical_file_name_in_backup*|バックアップ セット内のデータまたはログ ファイルの論理名を指定します。 バックアップ セット内のデータ ファイルまたはログ ファイルの論理ファイル名は、バックアップ セットが作成されたときのデータベース内における論理名と同じです。<br /><br /> <br /><br /> 注:バックアップ セットに含まれる論理ファイルの一覧を取得するには、[RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md) を使用します。|  
    |*operating_system_file_name*|*logical_file_name_in_backup*で指定したファイルの新しい場所を指定します。 ファイルはこの場所に復元されます。<br /><br /> 必要に応じて、 *operating_system_file_name* に復元するファイルの新しいファイル名を指定します。 これは、同じサーバー インスタンスで既存のデータベースのコピーを作成する場合に必要です。|  
    |*n*|追加の MOVE ステートメントを指定できることを示すプレースホルダーです。|  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、 `MyAdvWorks` サンプル データベースのバックアップを復元して、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] という名前の新しいデータベースを作成します。このデータベースには、2 つのファイル、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data と [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log が含まれます。 このデータベースは、単純復旧モデルを使用しています。 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースはサーバー インスタンスに既に存在するため、バックアップ内のファイルを新しい場所に復元する必要があります。 RESTORE FILELISTONLY ステートメントは、復元するデータベース内のファイル数と名前を判断するために使用します。 データベース バックアップは、バックアップ デバイスの 1 番目のバックアップ セットです。  
  
> **注:** 特定日時への復元を含む、トランザクション ログのバックアップと復元の例では、次の `MyAdvWorks_FullRM` の例と同様、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] から作成した `MyAdvWorks` データベースを使用します。 ただし、作成された `MyAdvWorks_FullRM` データベースは、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使って、完全復旧モデルを使用するように変更する必要があります:ALTER DATABASE <データベース名> SET RECOVERY FULL。  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの完全データベース バックアップを作成する方法の例については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)」を参照してください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [SSMS を使用してデータベース バックアップを復元する](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [バックアップと復元によるデータベースのコピー](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)  
  
  
