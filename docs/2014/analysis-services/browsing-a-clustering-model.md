---
title: クラスタ リング モデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b2662a08974c0eee0eed58b21d77421b3b75749
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66064679"
---
# <a name="browsing-a-clustering-model"></a>クラスター モデルの参照
  使用してクラスタ リング モデルを開くときに**参照**、クラスタ リングのビューアーに似た、対話型ビューアーでモデルが表示されます[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]します。 ビューアーは、作成されたクラスターを調査して、クラスターの特性を把握するのに役立ちます。 また、個々のセグメントを他のセグメントや母集団と比較対照することもできます。  
  
##  <a name="BKMK_Tabs"></a> モデルを調査します。  
 **参照**ウィンドウには、クラスタ リング モデルを理解し、基になるデータ グループの属性を調査するのに役立つ次のツールが含まれています。  
  
-   [クラスター ダイアグラム](#BKMK_ClusterDiagram)  
  
-   [クラスターのプロファイル](#BKMK_ClusterProfiles)  
  
-   [クラスターの特性](#BKMK_ClusterCharacteristics)  
  
-   [クラスターの識別](#BKMK_ClusterDiscrimination)  
  
 クラスタ リング モデルをテストするサンプル データを使用して、サンプル データ ブックのトレーニング タブで、使用してクラスター モデルを構築[クラスター ウィザード&#40;Excel 用データ マイニング アドインで&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)とすべての既定値.  
  
###  <a name="BKMK_ClusterDiagram"></a> クラスター ダイアグラム  
 **クラスター ダイアグラム** タブには、マイニング モデル内のすべてのクラスターが表示されます。 データセットに見つかった異なるグループの数、および、互いにどれぐらい近いか遠いかを確認できます。  
  
##### <a name="explore-the-cluster-diagram"></a>クラスター ダイアグラムの調査  
  
1.  ダイアグラムの [クラスター 1] をクリックします。  
  
     すべてのクラスターを接続する灰色の線が変化して、選択したクラスターにつながる線が明るい青色で強調表示されます。  
  
     ![クラスター ダイアグラムの紹介](media/dm13-cluster-diagram-intro.gif "クラスター ダイアグラムの紹介")  
  
     クラスターを結ぶ線の濃さは、クラスターの類似性の強度を表します。 網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。 線が濃くなるほど、2 つのクラスターの類似性が強いことを表します。  
  
2.  クラスター ダイアグラムの左側にあるスライダーをドラッグすると、ビューアーに表示される線の数を調整できます。  
  
     スライダーをドラッグして下げると、クラスター間で最も強いリンクだけが表示されます。 これは関連のあるグループを目立たせるのに役立ちます。  
  
3.  通知、**網掛け変数**の右上隅にあるコントロール、**クラスター ダイアグラム**ウィンドウ。  
  
     既定では、設定が**母集団**します。 つまり、クラスターの色が濃くなるほど、サポートが多いということです。  
  
4.  クラスターの上にマウス カーソルを置きます。  
  
     そのクラスターの母集団を含むツールヒントが表示されます。  
  
5.  をクリックして、**網掛け変数**ドロップダウン ボックスの一覧、**年齢**変数。 値の一覧が表示されるようにすると、**状態**テキスト ボックス。  
  
     このモデルへの入力として使用される Age 列には、連続する数値が含まれていますが、クラスタリングのために、アルゴリズムによって常に数値が分離されます。 ご覧のとおり、ビンまたはグループなど、アルゴリズムが作成されたを"非常に低い (\<= 27)"と"非常に高 (> = 63)"。  
  
6.  **状態**ドロップダウン リストで、**非常に高い**とダイアグラムの変化を確認します。  
  
     網掛け変数を変更することで、どのクラスターがこの対象の年齢層を多数含んでいるか、どのクラスターにこの年齢層の顧客が少ないかがひとめでわかります。  
  
     ![年齢を表示するクラスター ダイアグラムの変更](media/dm13-cluster-diagramshadebyage.gif "年齢を表示するクラスター ダイアグラムの変更")  
  
     網掛けが濃いほど、そのクラスターの対象属性の比率と値の分布が大きくなります。  
  
7.  網掛けはクラスターを見つける最も色の濃い、**網掛け変数**年齢に設定されている > 65 です。  
  
     そのクラスターの上にマウス カーソルを合わせます。  
  
     ツールヒントに表示される値は、このクラスターで 65 歳を超える顧客の人数です。  
  
8.  クラスターを右クリックして**クラスター名の変更**します。 など、わかりやすい新しい名前を入力**経由で 65**します。 新しい名前はモデルと共にサーバーに保存され、他のクラスター ビューでクラスターを識別するときに使用できます。  
  
 [ページのトップへ](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterProfiles"></a> クラスターのプロファイル  
 **クラスターのプロファイル** タブでは、一度にすべてのクラスターの構成を比較できます。 モデルに慣れる過程では、この機能から始めることをお勧めします。 このビューは後で、特定のクラスターの調査中に関連クラスターを見つける必要が生じた場合にも役立ちます。  
  
 **クラスターのプロファイル**はまた、クラスターが互いに異なる方法の適切な概要を示します。 そこで、このビューを使用して、各クラスターにわかりやすい名前を付けると便利です。  
  
##### <a name="explore-the-cluster-profiles"></a>クラスターのプロファイルの調査  
  
1.  職業のセルをクリックして、**状態**職業のすべての値の一覧を表示する列。  
  
2.  クラスターのプロファイルで [Occupation] (職業) の上にマウス カーソルを移動します。  
  
     ツールヒントに、そのクラスターの職業分布が表示されます。  
  
     ![ツール ヒントまたは凡例では、詳細な値を表示](media/dm13-cluster-profile-age-tooltip.gif "ヒントまたは凡例で、詳細な値を表示")  
  
     通知は、いくつかのクラスター (図 1) などの職業の一覧が完了していないと、一部の職業は、ラベルに置き換えられます**他**します。  
  
     これは仕様です。ヒストグラムで多数の小さなバーを区別するのは難しいためです。 既定での重要度が最も高いバーだけが保持される場合と、それ以外のバーは灰色にまとめ**他**バケット。  
  
     ヒストグラムに表示されるバーの数を変更するオプションを使用して、**ヒストグラム バー**します。  
  
3.  なお、**年齢**コラムでは、他のユーザーと異なる。 グラフで Age を表すダイヤモンドをクリックします。  
  
     Age 列はもともと連続する数値のみを含んでいました。 クラスター アルゴリズムでは不連続値が必要であるため、Age 列の数値は、値の分布に基づいて限られた数の年齢層にグループ分けされています。  
  
4.  クラスターのプロファイルでダイヤモンド グラフの 1 つをクリックします。  
  
     これらのダイヤモンド グラフは、ソース データが連続する数値を使用する場合にのみ表示されます。 ダイヤモンド グラフは、各クラスターでのその値の平均値と標準偏差など、便利な統計情報を示します。  
  
    -   ダイヤモンド グラフの線は、属性の値の範囲を表します。 も、値を表示、**状態**の左側にある列、**プロファイル**グラフ。  
  
    -   ダイヤモンドの中心は、ノードの平均値に配置されます。  
  
    -   ダイヤモンドの幅は、そのノードにおける属性の分散を表します。 そのため、ダイヤモンドの幅が狭いほど、そのノードでより正確な予測を作成できることを示します。  
  
5.  グラフを見やすく、すぐに表示および選択する必要はありません、クラスターを右クリックして**列の非表示**します。 これは、モデルから削除されるわけで、列を一時的に折りたたまれるだけです。  
  
     を非表示にしたクラスターを表示する をクリックし、列の境界線をドラッグしたりリストから、クラスター名を選択**クラスター**します。  
  
6.  属性一覧をスクロールして [Bike Buyer] (自転車購入者) を見つけ、[Yes] (はい) の値の割合が最も高いクラスターを見つけます。  
  
     クラスターの名前を変更する列見出しを右クリックして**クラスターの名前の変更**、および種類**自転車購入者**します。  
  
     新しいクラスター名は、モデルを再処理するまで、すべてのビューとサーバーで保持されます。  
  
     ![グラフを使いやすくするためにクラスターの名前を変更](media/dm13-cluster-rename.gif "グラフを使いやすくするためにクラスターの名前を変更")  
  
 **ヒント**  
  
-   そのクラスターの属性を重要度順に並べ替えるには、列見出しをクリックします。  
  
-   ビューアーで列の順序を変更するには、列をドラッグします。  
  
-   詳細な統計情報を表示するのには、プロファイル グラフの任意のセルをクリックして、**マイニング凡例**します。  
  
-   任意のセルを右クリックして**モデル列をドリルスルー**を Excel で新しいワークシートに基になるデータを出力します。  
  
-   クラスターの列見出しおよび選択を右クリックして**構造データへのドリルスルー**モデルに含まれていないクラスター メンバーの詳細についての詳細な情報を取得します。  
  
     たとえば、顧客をプロファイリングする場合する可能性があります、連絡先情報を基になるデータ (マイニング構造) のままが含まれていませんがモデルでは、分析に有用ではないため。 しかし、顧客がクラスターに割り当てられた後は、ドリルスルーを使用して詳細データを表示することができます。  
  
 [ページのトップへ](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterCharacteristics"></a> クラスターの特性  
 [クラスターの特性] ビューでは、単一のクラスターを本格的に調査して、どの属性がこのデータ グループの最も強い特性となっているかを調べることができます。  
  
##### <a name="explore-the-cluster-characteristics"></a>クラスターの特性の調査  
  
1.  選択、**経由で 65**からクラスター、**クラスター**一覧。  
  
     クラスターを選択した後、そのクラスターを構成する特性を詳細に確認することができます。  
  
     クラスターに含まれている属性は **[変数]** 列に表示され、属性の状態は **[値]** 列に表示されます。  
  
     属性の状態が色分けされたバーとして表される、このクラスターでの確率も、重要度の順序で並んでいる、**確率**列。  
  
     ![クラスタ リング モデルの特性](media/dm13-cluster-characteristics.gif "クラスタ リング モデルの特性")  
  
2.  をクリックして、**変数**属性、並べ替える列。  
  
     並べ替え変数を変更すると、収入や自動車所有のような変数について、グループ内での値の分布状況を簡単に確認できます。  
  
3.  クリックして**Excel にコピー**します。  
  
     新しいワークシートが、選択したクラスターの特性を含むブックに追加されます。  
  
4.  一覧から、別のクラスターを選択するようになりました**自転車購入者**します。  
  
5.  クリックして**Excel にコピー**します。  
  
     新しいクラスター特性グラフは、独自のワークシートに追加されます。 比較することで、次の手順で行いますが容易にできるように、その他のプロファイルと同じワークシート上に移動することができます。  
  
 **ヒント**  
  
-   65 経由でクラスターの顧客の主な特性は、製品を購入しないことに注意してください。 この理由を知るには、クラスターを参照してグループを比較します。または、デシジョン ツリー モデルや Naïve Bayes モデルなど、因果関係の調査に適したアルゴリズムを使用して関連モデルを作成します。  
  
-   このクラスター (またはすべてのクラスター) の属性と確率の完全な一覧を取得するには、クエリを作成します。 クラスター モデルに対するクエリの例については、次を参照してください。[クラスタ リング モデルのクエリ例](data-mining/clustering-model-query-examples.md)します。  
  
 [ページのトップへ](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterDiscrimination"></a> クラスターの識別  
 使用する、**クラスターの識別** タブに 2 つのクラスター間またはクラスターと、データ セット内の他のすべてのケースの属性を比較します。  
  
 このビューアーの機能を強調表示を比較しますそれに基づいて作成した Excel のサイド バイ サイドでのテーブルに、**クラスターの特性**ビュー。  
  
##### <a name="explore-cluster-discrimination"></a>クラスターの識別の調査  
  
1.  **[クラスター 1]** と **[クラスター 2]** の一覧を使用して、比較するクラスターを選択します。  
  
    -   [クラスター 1] ボックスでは [Over 65] (65 歳超) をクリックします。  
  
    -   [クラスター 2] ボックスでは、[Bike Buyers] (自転車購入者) をクリックします。  
  
     比較結果は次の図のようになります。  
  
     ![モデル内のクラスターを比較する](media/dm13-cluster-compareclusters.gif "モデル内のクラスターを比較します。")  
  
     実際には、それに注意してください、**クラスターの識別**ビューアー複雑なクエリを比較しやすいように、2 つのグループを区別で最も重要な属性を抽出する、データ マイニング サーバーに送信します。顧客の 2 つのセット。  
  
2.  いずれかのクリックして、 **~ を優先しています.** 列。  
  
     属性と値一覧の右側にあるバーは、選択したクラスターの特性として、どの特徴または値が最も重要かを示しています。  
  
3.  今度は Excel で一覧を比較します。  
  
     ![アソシエーション モデルの依存関係ネットワーク グラフ](media/dm13-comparing-profiles-in-excel.gif "アソシエーション モデルの依存関係ネットワーク グラフ")  
  
     ビューアーで画像の作成に使用された基になる統計は、テーブルとして Excel に保存されるため、フィルターと並べ替え、実際の確率値の表示ができます。  
  
     Excel の使用に加えて、Visio 用のクラスター ビューアーを試すことをお勧めします。データ ポイントを表示できる他に、グラフを全面的に変更し強化することもできます。 詳細については、次を参照してください。[クラスター ダイアグラムのチュートリアル&#40;データ マイニング アドインで&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md)します。  
  
 **ヒント**  
  
 顧客のグループには、いくつかインサイトを取得した後にを使用してお試し、 [What-If シナリオ&#40;Excel 用テーブル分析ツール&#41;](what-if-scenario-table-analysis-tools-for-excel.md)または[ゴール シーク シナリオ&#40;Excel 用テーブル分析ツール&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)ツールは、結果に影響する変更可能性のあるモデルの要因を調査します。  
  
## <a name="see-also"></a>参照  
 [Excel におけるモデルの参照&#40;SQL Server データ マイニング アドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)   
 [クラスター ウィザード&#40;データ マイニング Excel 用アドイン&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
