---
title: アプリ展開の拡張機能
titleSuffix: SQL Server big data clusters
description: Python または R スクリプトをアプリケーションとして[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (プレビュー) にデプロイします。
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 49a59650c406e3b48394da45ad0eeb4589fc4374
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653602"
---
# <a name="how-to-use-visual-studio-code-to-deploy-applications-to-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Visual Studio Code を使用してアプリケーションを展開する方法[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、アプリ展開拡張機能で Microsoft Visual Studio コードを使用して SQL Server ビッグデータクラスターにアプリケーションをデプロイする方法について説明します。 この機能は CTP 2.3 で導入されました。 

## <a name="prerequisites"></a>前提条件

- [Visual Studio Code](https://code.visualstudio.com/)
- [ビッグデータクラスターの SQL Server](big-data-cluster-overview.md)CTP 2.3 以降

## <a name="capabilities"></a>Capabilities

この拡張機能では、Visual Studio Code での次のタスクがサポートされます。

- SQL Server ビッグ データ クラスターを使用して認証する。
- サポートされているランタイムの展開用に、GitHub リポジトリからアプリケーション テンプレートを取得する。
- ユーザーのワークスペースで現在開かれているアプリケーション テンプレートを管理する。
- YAML 形式の仕様を使用してアプリケーションを展開する。
- 展開したアプリを SQL Server ビッグ データ クラスター内で管理する。
- 展開したすべてのアプリと追加情報をサイド バーに表示する。
- 実行仕様を生成してアプリを使用するか、クラスターからアプリを削除する。
- 展開したアプリを YAML の実行仕様を通じて使用する。

以下のセクションでは、インストール プロセスについて説明し、拡張機能の動作の概要を示します。 

### <a name="install"></a>インストール

まず、Visual Studio Code にアプリ展開拡張機能をインストールします。

1. [アプリのデプロイ拡張機能](https://aka.ms/app-deploy-vscode)をダウンロードして、Visual Studio Code の一部として拡張機能をインストールします。

1. Visual Studio Code を起動し、[拡張機能] サイドバーに移動します。

1. サイド バーの上部にある [`…`] コンテキスト メニューをクリックし、[`Install from vsix`]\(vsix からのインストール\) を選択します。

   ![VSIX のインストール](media/vs-extension/install_vsix.png)

1. ダウンロードした `sqlservbdc-app-deploy.vsix` ファイルを検索し、それを選択してインストールします。

SQL Server ビッグデータクラスターアプリ展開拡張機能がインストールされると、Visual Studio Code の再読み込みを求めるメッセージが表示されます。 Visual Studio Code サイドバーに SQL Server BDC アプリエクスプローラーが表示されます。

### <a name="app-explorer"></a>アプリ エクスプローラー

サイド バーの拡張機能をクリックして、アプリ エクスプローラーが表示されているサイド パネルを読み込みます。 次のアプリ エクスプローラーのサンプル スクリーンショットは、利用できるアプリやアプリの仕様がないことを示しています。

![アプリ エクスプローラー](media/vs-extension/app_explorer.png)

#### <a name="connect-to-cluster"></a>クラスターへの接続

クラスター エンドポイントに接続するには、次のいずれかの方法を使用します。

- 下部にある、[`SQL Server BDC Disconnected`]\(SQL Server BDC が切断されました\) と示されているステータス バーをクリックします。
- または、上部にある、出口をさす矢印の付いた `Connect to Cluster` [新しい接続] ボタンをクリックします。

Visual Studio Code、適切なエンドポイント、ユーザー名、およびパスワードの入力を求められます。

接続するエンドポイントは、 `Cluster Management Service`ポート30080のエンドポイントです。

このエンドポイントは、コマンドラインから 

```
azdata bdc endpoint list
```

この情報を取得する他の方法の1つとして、Azure Data Studio でサーバーの **[管理]** を右クリックして、一覧表示されているサービスのエンドポイントを確認する方法があります。

![広告エンドポイント](media/vs-extension/ads_end_point.png)

使用するエンドポイントが見つかったら、クラスターに接続します。

![新しい接続](media/vs-extension/connect_to_cluster.png)

 正しい資格情報とアプリエンドポイントが指定されている場合、Visual Studio Code はクラスターに接続されたことを通知し、展開されたアプリがサイドバーに表示されることを確認します。 正常に接続すると、エンドポイントとユーザー名がユーザー プロファイルの一部として `./sqldbc` に保存されます。 パスワードやトークンは保存されません。 もう一度ログインすると、保存されているホストとユーザー名がプロンプトに事前に入力されますが、パスワードは常に入力する必要があります。 別のクラスター エンドポイントに接続する場合は、`New Connection` [新しい接続] をもう一度クリックします。 Visual Studio Code を閉じるか、別のワークスペースを開いて再接続する必要がある場合、接続は自動的に閉じられます。

### <a name="app-template"></a>アプリ テンプレート

アプリのアーティファクトを保存する Visual Studio Code で*ワークスペースを開く*必要があります。

いずれかのテンプレートから新しいアプリを展開するには、[`App Specifications`]\(アプリの仕様\) ウィンドウの [`New App Template`]\(新しいアプリ テンプレート\) ボタンをクリックします。このボタンをクリックすると、名前、ランタイム、およびローカル コンピューターで新しいアプリを配置する場所を入力するように求められます。 指定する名前とバージョンは、DNS-1035 ラベルであり、小文字の英数字または '-' で構成されている必要があります。また、アルファベット文字で始まり、英数字で終わる必要があります。

拡張機能のすべての機能を使用できるように、現在の Visual Studio Code ワークスペースに配置することをお勧めしますが、ローカルファイルシステムの任意の場所に配置することもできます。

![新しいアプリ テンプレート](media/vs-extension/new_app_template.png)

完了すると、指定した場所に新しいアプリケーションテンプレートがスキャフォールディングされ、ワークスペースに `spec.yaml` の展開が開きます。 選択したディレクトリがワークスペース内にある場合は、それが [`App Specifications`]\(アプリの仕様\) ウィンドウにも表示されます。

![読み込まれたアプリ テンプレート](media/vs-extension/loading_app_template.png)

このテンプレートは、[ `helloworld`アプリの仕様] ウィンドウで次のようにレイアウトされた単純なアプリです。

- **spec. yaml**
   - アプリの展開方法をクラスターに指示します
- **run-spec.yaml**
   - アプリの呼び出し方法をクラスターに指示します

アプリのソースコードは、ワークスペースフォルダーにあります。

- **ソースファイル名**
   - これは、`spec.yaml` で `src` に指定されているソース コード ファイルです。
   - `spec.yaml` に示されているように、アプリの `entrypoint` と見なされる `handler` という 1 つの関数があります。 `msg` という文字列の入力を受け取り、`out` という文字列の出力を返します。 これらは `spec.yaml` の `inputs` と `outputs` で指定されます。

スキャフォールディング テンプレートが不要で、既に作成済みのアプリの展開用に `spec.yaml` を優先する場合は、[`New App Template`]\(新しいアプリ テンプレート\) ボタンの横にある [`New Deploy Spec`]\(新しい展開の仕様\) ボタンをクリックして同じプロセスを実行しますが、`spec.yaml` が表示されるだけです。それにより選択方法を変更できます。

### <a name="deploy-app"></a>アプリを展開

このアプリは、`spec.yaml` 内の [`Deploy App`]\(アプリの展開\) の CodeLens によってすぐに展開することも、[App Specifications]\(アプリの仕様\) メニューで `spec.yaml` ファイルの横にある稲妻フォルダーのボタンを押すこともできます。 拡張機能により、`spec.yaml` を配置したディレクトリ内のすべてのファイルが zip 圧縮され、アプリがクラスターに展開されます。 

>[!NOTE]
>すべてのアプリ ファイルが確実に `spec.yaml` と同じディレクトリにあるようにします。 `spec.yaml` は、アプリのソース コード ディレクトリのルート レベルにある必要があります。 

![アプリの展開のボタン](media/vs-extension/deploy_app_lightning.png)

![アプリの展開の CodeLens](media/vs-extension/deploy_app_codelens.png)

サイド バーのアプリの状態に基づいてアプリの使用準備が整うと、通知が表示されます。

![展開済みアプリ](media/vs-extension/app_deploy.png)

![アプリ準備完了のサイド バー](media/vs-extension/app_ready_side_bar.png)

![アプリ準備完了通知](media/vs-extension/app_ready_notification.png)

サイド ウィンドウでは、次のものが使用可能なことを確認できます。

展開したすべてのアプリを次の情報と共にサイド バーで確認できます。

- 状態
- version
- 入力パラメーター
- 出力パラメーター
- リンク
  - Swagger
  - 詳細

をクリック`Links`すると、デプロイされたアプリのに`swagger.json`アクセスできることがわかります。これにより、アプリを呼び出す独自のクライアントを作成できます。

![Swagger](media/vs-extension/swagger.png)

詳細については、「[ビッグ データ クラスターでアプリケーションを使用する](big-data-cluster-consume-apps.md)」を参照してください。

### <a name="app-run"></a>アプリ実行

アプリの準備ができたら、アプリ テンプレートの一部として指定された `run-spec.yaml` を使用して、アプリを呼び出します。

![実行仕様](media/vs-extension/run_spec.png)

`hello` の代わりに任意の文字列を指定してから、CodeLens リンクまたは `run-spec.yaml` の横にあるサイド バーの稲妻ボタンを使用して、もう一度実行します。 何らかの理由で実行仕様がない場合は、クラスター内の展開済みアプリから生成します。

![実行仕様の取得](media/vs-extension/get_run_spec.png)

それを手に入れて満足するまで編集したら、実行します。 アプリの実行が完了すると、Visual Studio Code によって適切なフィードバックが返されます。

![アプリの出力](media/vs-extension/app_output.png)

上記からわかるように、出力はワークスペース内の一時的な `.json` ファイルで提供されます。 この出力を保持する場合は、保存してください。そうしないと、終了時に削除されます。 アプリにファイルに書き込む出力がない場合、[`Successful App Run`]\(アプリの正常な実行\) 通知のみが下部に表示されます。 正常に実行されなかった場合は、問題を特定するのに役立つ適切なエラー メッセージが表示されます。

アプリを実行するときは、さまざまな方法でパラメーターを渡すことができます。

`.json` を使用して、要求されるすべての入力を指定できます。これは次のとおりです。

- `inputs: ./example.json`

展開されたアプリを呼び出すときに、入力パラメーターがアプリに本来備わっているかユーザーが指定したものである場合、または入力パラメーターがプリミティブ以外のもの (配列、ベクター、データフレーム、複雑な JSON など) である場合、アプリを呼び出すときにパラメーターの型を行に直接指定します。次のようになります。

- ベクター
    - `inputs:`
        - `x: [1, 2, 3]`
- マトリックス
    - `inputs:`
        - `x: [[A,B,C],[1,2,3]]`
- オブジェクト
    - `inputs:`
        - `x: {A: 1, B: 2, C: 3}`

または、必須の入力をアプリに必要な形式で指定した `.txt`、`.json`、`.csv` に対する相対ファイル パスまたは絶対ファイル パスとして文字列を指定します。 ファイルの解析は、`Node.js Path library` に基づきます。ここでは、ファイル パスは`string that contains a / or \ character` / または \ 文字を含む文字列として定義されています。

必要に応じた入力パラメーターが指定されていない場合、正しくないファイル パス (文字列ファイルのパスが指定されていた場合) またはパラメーターが無効であったことを示す適切なエラー メッセージが表示されます。 アプリの作成者には、定義しているパラメーターを確実に理解する責任があります。

アプリを削除するには、[`Deployed Apps`]\(展開済みアプリ\) サイド ウィンドウでアプリの横にあるごみ箱ボタンをクリックするだけです。

## <a name="next-steps"></a>次の手順

「[ビッグデータクラスターでアプリケーション](big-data-cluster-consume-apps.md)を[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]使用する」で、独自のアプリケーションにデプロイされているアプリを統合する方法について詳しく説明します。 「[アプリ展開のサンプル](https://aka.ms/sql-app-deploy)」にある追加のサンプルを参照して、拡張機能を試してみることもできます。

の詳細[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]について[は[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md)、「」を参照してください。


私たちの目標は、この拡張機能をお客様にとって有益なものにすることです。フィードバックをお待ちしております。 [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] チーム](https://aka.ms/sqlfeedback)までお送りください。
