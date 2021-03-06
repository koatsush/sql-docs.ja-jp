---
title: SQL レプリケーションのスナップショットの初期化オプションを変更する | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 9bef4e304b592a6be1c9d59c44d691e07829d70f
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768370"
---
# <a name="modify-snapshot-initialization-options-for-sql-replication"></a>SQL レプリケーションのスナップショットの初期化オプションを変更する 
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

[ スナップショットを使用してサブスクリプションを初期化する](initialize-a-subscription-with-a-snapshot.md)際には、いくつかのオプションを指定できます。

## <a name="specify-snapshot-format-sql-server-management-studio"></a>スナップショットの形式の指定 (SQL Server Management Studio)
  スナップショットの形式は、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで指定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
### <a name="to-specify-snapshot-format"></a>スナップショットの形式を指定するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、 **[ネイティブ SQL Server - サブスクライバーはすべて SQL Server を実行しているサーバーである必要があります]** または **[文字 - パブリッシャーまたはサブスクライバーで SQL Server が実行されていない場合は必須]** を選択します。  
  
    > [!NOTE]  
    >  このパブリケーションで SQL Server Compact データベースまたは SQL Server 以外のデータベースへのサブスクリプションをサポートする必要がある場合を除き、ネイティブ形式を選択することをお勧めします。  
  
2.  **[OK]** を選択します。   

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="snapshot-folder-locations"></a>スナップショット フォルダーの場所

### <a name="default-snapshot-location"></a>既定のスナップショットの場所
ディストリビューションの構成ウィザードの **[スナップショット フォルダー]** ページで、既定のスナップショットの場所を指定します。 ウィザードの使用の詳細については、「[パブリッシングおよびディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)」を参照してください。 ディストリビューターとして構成されていないサーバーでパブリケーションを作成する場合は、パブリケーションの新規作成ウィザードの **[スナップショット フォルダー]** ページで既定のスナップショットの場所を指定します。 このウィザードの使用の詳細については、「[パブリケーションの作成](../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
 **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、既定のスナップショットの場所を変更します。 詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、各パブリケーションのスナップショット フォルダーを設定します。 詳しくは、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」をご覧ください。  
  
### <a name="to-modify-the-default-snapshot-location"></a>既定のスナップショットの場所を変更するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、既定のスナップショットの場所を変更するパブリッシャーのプロパティ ボタン ( **[...]** ) をクリックします。    
2.  **[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックスで、 **[既定のスナップショット フォルダー]** プロパティの値を入力します。  
  
    > [!NOTE]  
    >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\snapshot など) で指定する必要があります。 詳細については、「[Secure the Snapshot Folder](../../relational-databases/replication/security/secure-the-snapshot-folder.md)」(スナップショット フォルダーのセキュリティ保護) をご覧ください。    
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
 

### <a name="alternate-snapshot-locations"></a>スナップショットの場所を変更する
スナップショットの代替位置を使用すると、既定の場所 (通常はディストリビューター上) 以外の場所、または既定の場所に加えて別の場所にスナップショット ファイルを格納できます。 代替位置には、別のサーバー、ネットワーク ドライブ、またはリムーバブル メディア (CD-ROM またはリムーバブル ディスクなど) を指定できます。  
  
スナップショットの代替位置は、パブリケーションのプロパティとして格納されます。 スナップショットの代替位置はパブリケーション プロパティであるため、ディストリビューション エージェントおよびマージ エージェントは同期処理の過程で適切なスナップショットを見つけることができます。  
  
代替スナップショット フォルダーを指定する必要がある場合、またはスナップショット ファイルを圧縮する必要がある場合には、パブリケーションの作成時に即座に初期スナップショットを作成せず、スナップショットの場所に関するパブリケーションのプロパティを設定してから、そのパブリケーションにスナップショット エージェントを実行してください。 初期スナップショットの作成後に代替位置を変更した場合、パブリケーションに対して生成されたすべてのスナップショットは、新しい代替位置には再配置されません。 この場合、パブリケーションの設定に応じて、マージ エージェントとディストリビューション エージェントが新しい代替位置でスナップショット ファイルを見つけることができなくなる可能性があります。  
  
> [!NOTE]  
>  ( **[パブリケーション プロパティ]** ダイアログ ボックスまたは [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) を使用して、) 既定のスナップショット フォルダーと同じ場所に代替位置を指定しないでください。  
  
> [!CAUTION]  
>  WebSync と代替スナップショット フォルダーの場所を同時に使用しないでください。  
  
#### <a name="use-sql-server-management-studio"></a>SQL Server Management Studio の使用 [SQL Server]
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、以下の操作を実行します。  
  
    1.  **[ファイルを次のフォルダーに保存する]** チェック ボックスをオンにし、 **[参照]** をクリックしてディレクトリに移動するか、スナップショット ファイルの格納先ディレクトリへのパスを入力します。  
  
        > [!NOTE]  
        >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\snapshot など) で指定する必要があります。 詳細については、「[Secure the Snapshot Folder](../../relational-databases/replication/security/secure-the-snapshot-folder.md)」(スナップショット フォルダーのセキュリティ保護) をご覧ください。  
  
    2.  スナップショット ファイルを既定のフォルダーにも書き込む必要がない限り、 **[ファイルを既定のフォルダーに保存する]** チェック ボックスはオフにしてください。  
  
     スナップショット ファイルを圧縮するには、 **[スナップショット ファイルをこのフォルダーに圧縮]** を選択します。 圧縮は通常、低帯域幅接続を使用する場合や、スナップショットの代替位置をリムーバブル メディア (CD-ROM など) にする場合に使用します。  
  
2.  **[OK]** を選択します。  
  
#### <a name="use-transact-sql"></a>Transact-SQL の使用 

[スナップショット プロパティを設定する &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md) ときは、**snapshot_in_defaultfolder** の値を false に指定します。 

## <a name="compressed-snapshots"></a>圧縮スナップショット
  低速なネットワークでスナップショットを転送する場合や、スナップショットをリムーバブル メディアに保存する際にそのままではメディアに収まらない場合は、スナップショット ファイルを圧縮することができます。 スナップショット ファイルを圧縮すると、このような場合に役に立つ反面、スナップショットの生成および適用に要する時間が増大します。  
  
 圧縮スナップショット ファイルは [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB ファイル形式で書き込まれます。このファイル形式では 2 GB 以下のファイルを圧縮できます (スナップショット ファイルのサイズが 2 GB を超える場合は圧縮できません)。 ファイルを圧縮するには、代替スナップショット フォルダーにファイルを書き込む必要があります (既定のスナップショット フォルダーに書き込まれるファイルは圧縮できません)。 
  
 ファイルは、ディストリビューション エージェントまたはマージ エージェントが実行されている場所で圧縮解除されます。一般にプル サブスクリプションで圧縮スナップショットを使用する場合、サブスクライバーでファイルの圧縮が解除されるようにします。 サブスクライバーが圧縮ファイルを受信すると、そのファイルは最初は一時的な場所に書き込まれます。 圧縮ファイルがサブスクライバーにコピーされた後、圧縮ファイル内のスナップショット ファイルは CAB ユーティリティによって 1 ファイルずつ順番に圧縮解除されます。 サブスクライバーで必要な空き容量は、圧縮ファイルと圧縮されていない最大のファイルを合計したサイズと同じです。  
  
> [!NOTE]  
>  圧縮スナップショットを使用すると、ネットワーク経由でスナップショット ファイルを移動する際のパフォーマンスが向上する場合があります。 ただし、スナップショットを圧縮すると、スナップショット ファイル生成時のスナップショット エージェント、およびスナップショット ファイル適用時のディストリビューション エージェントまたはマージ エージェントで、追加の処理が必要になります。 これにより、スナップショット生成が遅くなり、スナップショットを適用するための時間が延びることもあります。 また、ネットワークに障害が発生した場合、圧縮スナップショットを復旧することはできません。したがって、信頼性の低いネットワークには向いていません。 ネットワーク経由で圧縮スナップショットを使用するときは、これらのトレードオフを慎重に検討してください。  
  
### <a name="use-sql-server-management-studio"></a>SQL Server Management Studio の使用 [SQL Server]
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、以下の操作を実行します。  
  
    1.  **[ファイルを次のフォルダーに保存する]** チェック ボックスをオンにし、 **[参照]** をクリックしてディレクトリに移動するか、スナップショット ファイルの格納先ディレクトリへのパスを入力します。  
  
        > [!NOTE]  
        >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\snapshot など) で指定する必要があります。 詳細については、「[Secure the Snapshot Folder (スナップショット フォルダーのセキュリティ保護)](security/secure-the-snapshot-folder.md)」をご覧ください  
  
    2.  スナップショット ファイルを既定のフォルダーにも書き込む必要がない限り、 **[ファイルを既定のフォルダーに保存する]** チェック ボックスはオフにしてください。  
  
        > [!NOTE]  
        >  このチェック ボックスをオンにした場合、既定のフォルダーに格納されたファイルは圧縮されません。 圧縮されたファイルは、上記の手順で別途指定した場所にのみ格納できます。  
  
2.  **[スナップショット ファイルをこのフォルダーに圧縮]** チェック ボックスをオンにします。    
3.  **[OK]** を選択します。   

### <a name="use-transact-sql"></a>Transact-SQL の使用

[スナップショット プロパティを構成する](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)ときは、**compress_snapshot** の値を **True** に指定します。 

## <a name="execute-scripts-before-and-after-snapshot-is-applied"></a>スナップショットが適用される前および後のスクリプトの実行
スナップショットが適用される前または後に、スクリプトを指定してサブスクライバーで実行できます。 スクリプトは、各サブスクライバーでのログインの作成やスキーマ (オブジェクト所有者) の作成など、さまざまな理由で使用できます。  
  
 各スクリプトに対してファイルの場所を指定すると、スナップショットの処理が行われるたびに、スナップショット エージェントはスクリプト ファイルを現在のスナップショット フォルダーにコピーします。 ディストリビューション エージェントまたはマージ エージェントは、スナップショットを適用するときに、レプリケートされたオブジェクト スクリプトの前にプリスナップショット スクリプトを実行します。 ディストリビューション エージェントまたはマージ エージェントは、他のすべてのレプリケートされたオブジェクト スクリプトおよびデータが適用された後にポストスナップショット スクリプトを実行します。 スナップショットの適用が完了し、スクリプト ファイルが正常に実行された後、スクリプト ファイルはサブスクライバー上の作業ディレクトリから削除されます。  
  
 スクリプトは、 **sqlcmd** ユーティリティを起動することで実行されます。 スクリプトを配置する前に、 **sqlcmd** を使用して実行し、想定どおりに実行されることを確認します。 スナップショットが適用される前後に実行されるスクリプトの内容は、繰り返し使用できる必要があります。 たとえば、スクリプト内でテーブルを作成する場合、最初にテーブルの存在を確認し、そのテーブルが存在する場合に適切な動作を行う必要があります。 既にスクリプトが適用されているサブスクリプションを再初期化する必要がある場合、スクリプトは繰り返し使用できる必要があります。再初期化中に新しいスナップショットを適用すると、そのスクリプトが再度適用されるためです。  
  
 スナップショット ファイルを圧縮し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB ファイル形式にする場合は、スクリプトも圧縮され、CAB ファイルに格納されます。 圧縮スナップショット ファイルがサブスクライバーに転送され、サブスクライバー上の作業ディレクトリで圧縮解除された後は、プリスナップショット スクリプトとして指定されたスクリプトが実行されます。 同じように、ポストスナップショット スクリプトは、スナップショット適用の最後のステップとしてサブスクライバーで解凍および実行されます。  

### <a name="execute-a-script"></a>スクリプトの実行 

1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、以下の操作を実行します。    
    -   スナップショット適用前に実行するスクリプトを指定するには、 **[参照]** をクリックしてスクリプトに移動するか、 **[スナップショットの適用前に以下のスクリプトを実行]** ボックスにスクリプトへのパスを入力します。  
  
        > [!NOTE]  
        >  ディストリビューション エージェントまたはマージ エージェントは、指定するディレクトリに対し、読み取り権限を持つ必要があります。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\scripts\myscript.sql など) で指定する必要があります。  
  
    -   スナップショット適用後に実行するスクリプトを指定するには、 **[参照]** をクリックしてスクリプトに移動するか、 **[スナップショットの適用後に以下のスクリプトを実行]** ボックスにスクリプトへの UNC パスを入力します。   
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  


## <a name="see-also"></a>参照  
 [Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [FTP によるスナップショットの転送](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)   
 [スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)     
  
  
