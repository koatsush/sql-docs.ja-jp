---
title: コントローラーとは
titleSuffix: SQL Server big data clusters
description: この記事では、 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]のコントローラーについて説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 643cb2b4e252e1818940bda2be54917c23cefe06
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652286"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>SQL Server ビッグ データ クラスターのコントローラーとは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このコントローラーでは、ビッグ データ クラスターを展開および管理するコア ロジックがホストされます。 Kubernetes、クラスターの一部である SQL Server インスタンス、および HDFS や Spark などのその他のコンポーネントとのすべてのやり取りがここで処理されます。

コントローラー サービスには、次のコア機能があります。

- クラスターのライフサイクルの管理: クラスターのブートストラップと削除、構成の更新
- マスター SQL Server インスタンスを管理する
- コンピューティング、データ、および記憶域プールを管理する
- クラスターの状態を観察する監視ツールを公開する
- 予期しない問題を検出して修復するトラブルシューティング ツールを公開する
- クラスターのセキュリティを管理する:
  - クラスター エンドポイントを確実にセキュリティで保護する
  - ユーザーとロールを管理する
  - クラスター内通信用の資格情報を構成する

## <a name="deploying-the-controller-service"></a>コントローラー サービスを展開する

このコントローラーは、お客様がビッグ データ クラスターを構築する場合と同じ Kubernetes 名前空間で展開およびホストされます。 このサービスは、クラスターのブートストラップ中に、Kubernetes 管理者によって **azdata** コマンドライン ユーティリティを使用してインストールされます。 詳細については[ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ](deploy-get-started.md)、「」を参照してください。

ビルドアウト ワークフローは、「[概要](big-data-cluster-overview.md)」の記事で説明されているすべてのコンポーネントを含む Kubernetes の完全に機能する SQL Server ビッグ データ クラスター上にレイアウトします。 ブートストラップ ワークフローでは、まずコントローラー サービスが作成されます。これが展開されると、コントローラー サービスによって、マスター、コンピューティング、データ、および記憶域プールの残りのサービス部分のインストールと構成が調整されます。

## <a name="managing-the-cluster-through-the-controller-service"></a>コントローラー サービスを使用してクラスターを管理する

いずれかの **azdata** コマンドを使用して、コントローラー サービスを介してクラスターを管理できます。 ポッドのような追加の Kubernetes オブジェクトを同じ名前空間に展開しても、コントローラー サービスによって管理または監視されません。 **kubectl** コマンドを使用して、Kubernetes レベルでクラスターを管理することもできます。 詳細については、「[監視[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]とトラブルシューティング](cluster-troubleshooting-commands.md)」を参照してください。

ビッグ データ クラスター用に作成されたコントローラーと Kubernetes オブジェクト (ステートフル セット、ポッド、シークレットなど) は、専用の Kubernetes 名前空間に存在します。 コントローラー サービスには、その名前空間内のすべてのリソースを管理するために、Kubernetes クラスター管理者によってアクセス許可が付与されます。  このシナリオの RBAC ポリシーは、**azdata** を使用して初期クラスター展開の一部として自動的に構成されます。

### <a name="azdata"></a>azdata

**azdata** は Python で記述されたコマンドライン ユーティリティです。これを使用すると、クラスター管理者は、コントローラー サービスによって公開されている REST API を使用して、ビッグ データ クラスターをブートストラップして管理することができます。

## <a name="controller-service-security"></a>コントローラー サービスのセキュリティ

コントローラー サービスへのすべての通信は、HTTPS 経由の REST API を介して行われます。 自己署名証明書は、ブートストラップ時に自動的に生成されます。 

コントローラー サービス エンドポイントへの認証は、ユーザー名とパスワードに基づいています。 これらの資格情報は、環境変数 `CONTROLLER_USERNAME` および `CONTROLLER_PASSWORD` の入力を使用して、クラスターのブートストラップ時にプロビジョニングされます。

> [!NOTE]
> [SQL Server パスワードの複雑さの要件](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017)に準拠したパスワードを指定する必要があります。

## <a name="next-steps"></a>次の手順

の[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]詳細については、次のリソースを参照してください。

- [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]概要](big-data-cluster-overview.md)
- [ワークショップ: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]のアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
