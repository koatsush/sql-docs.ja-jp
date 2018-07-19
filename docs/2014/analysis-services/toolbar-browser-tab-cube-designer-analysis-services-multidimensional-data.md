---
title: ツールバー ([ブラウザー] タブ、キューブ デザイナー) (Analysis Services - 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a1c6272d-e514-456b-9995-b73fec0112a2
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d0735af06261d606888fe04d45e968b63f5d6403
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300922"
---
# <a name="toolbar-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>ツール バー (キューブ デザイナーの [ブラウザー] タブ) (Analysis Services - 多次元データ)
  キューブ デザイナーの**ツール バー**にある機能は、キューブやそのオブジェクトをデザインまたは参照しているときと、MDX クエリを作成しているときに使用する共通の操作を実行するときに使用します。 デザイン時とクエリ ビューの両方に共通する操作としては、ユーザー コンテキストの設定、オブジェクトの処理、既定の言語の設定などがあります。  
  
 **ツール バー** のボタンとその機能を次の表に示します。  
  
|ボタン|説明|  
|------------|-----------------|  
|**[テキストとして編集]**|このデータ ソースの種類では使用できません。|  
|**[インポート]**|ファイル システムのレポート定義 (.rdl) ファイルから既存のクエリをインポートします。|  
|![MDX クエリ ビューに変更](media/rsqdicon-commandtypemdx.gif "MDX クエリのビューへの変更")|コマンドの種類を MDX に切り替えます。|  
|![結果データの更新](media/rsqdicon-refresh.gif "結果データの更新")|データ ソースからメタデータを更新します。|  
|![計算されるメンバーの追加](media/rsqdicon-addcalculatedmember.gif "計算されるメンバーの追加")|**[計算されるメンバー ビルダー]** ダイアログ ボックスを表示します。|  
|![空のセルの表示の切り替え](media/rsqdicon-showemptycells.gif "空のセルの表示の切り替え")|データ ペインに空のセルを表示するかどうかを切り替えます。 これは、MDX で NON EMPTY 句を使用することに相当します。|  
|![クエリの自動実行](media/rsqdicon-autoexecute.gif "クエリの自動実行")|クエリを自動的に実行し、変更が生じるたびに結果を表示します。 結果はデータ ペインに表示されます。|  
|![集計ボタンの表示](media/rsqdicon-showaggregations.gif "集計ボタンの表示")|集計をデータ ペインに表示します。|  
|![削除](media/rsqdicon-delete.gif "削除")|データ ペインで選択した列をクエリから削除します。|  
|![[クエリ パラメーター] ダイアログ ボックスのアイコン](media/iconqueryparameter.gif "[クエリ パラメーター] ダイアログ ボックスのアイコン")|**[クエリ パラメーター]** ダイアログ ボックスを表示します。 クエリ パラメーターの値を指定する場合、同じ名前のパラメーターが自動的に作成されます。|  
|![[クエリの準備] ボタン](media/rsqdicon-preparequery.gif "[クエリの準備] ボタン")|クエリを準備します。|  
|![クエリを実行する](media/rsqdicon-run.gif "クエリを実行する")|クエリを実行し、結果をデータ ペインに表示します。|  
|![クエリを取り消す](media/rsqdicon-cancel.gif "クエリを取り消す")|クエリを取り消します。|  
|![デザイン モードに切り替える](media/rsqdicon-designmode.gif "デザイン モードに切り替える")|デザイン モードとクエリ モードを切り替えます。|  
  
 一般に、 **デザイン モード** でも **クエリ モード**でも、ツール バーのボタンは共通です。 ただし、次のボタンは、クエリ モードでは有効になっていません。  
  
-   **[テキストとして編集]**  
  
-   **計算されるメンバーを追加**(![計算されるメンバーの追加](media/rsqdicon-addcalculatedmember.gif "計算されるメンバーの追加"))  
  
-   **空のセルを表示する** (![空のセルの表示の切り替え](media/rsqdicon-showemptycells.gif "空のセルの表示の切り替え"))  
  
-   **自動実行** (![クエリの自動実行](media/rsqdicon-autoexecute.gif "クエリの自動実行"))  
  
-   **集計の表示** (![集計ボタンの表示](media/rsqdicon-showaggregations.gif "集計ボタンの表示"))  
  
## <a name="options"></a>および  
  
|オプション|説明|  
|------------|-----------------|  
|**[処理]**|クリックすると、 **[処理]** ダイアログ ボックスを表示して、キューブを処理できます。 **[処理]** ダイアログ ボックスの詳細については、「[[処理] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。|  
|**ユーザーの変更**|**[セキュリティ コンテキスト]** ダイアログ ボックスを表示し、**[ブラウザー]** タブで使用されているユーザーおよびロールを変更します。**[セキュリティ コンテキスト]** ダイアログ ボックスの詳細については、「[[セキュリティ コンテキスト] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](security-context-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。|  
|**再接続**|接続が失われたりタイムアウトしたりしたために **[ブラウザー]** タブに対するセッションが切断された場合に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [計算] **タブを** インスタンスおよびキューブを含むデータベースに再接続します。|  
|**[更新]**|**[メタデータ]** ペインおよび **[レポート]** ペインの表示を最新の情報に更新します。|  
|**[昇順で並べ替え]**|**[レポート]** ペイン内の選択行の兄弟を、**[言語]** で指定された言語に対して昇順で並べ替えます。<br /><br /> **注** このオプションは、**[レポート]** ペイン内のセルが選択されている場合にのみ有効です。|  
|**[降順で並べ替え]**|**[レポート]** ペイン内の選択行の兄弟を、 **[言語]** で指定された言語に対して降順で並べ替えます。<br /><br /> 注: このオプションは、 **[レポート]** ペイン内のセルが選択されている場合にのみ有効です。|  
|**自動フィルター**|**[結果]** ペイン内の結果を自動的にフィルター処理します。|  
|**上/下ののみを表示します。**|値またはパーセントを選択し、選択されたメジャーに基づいて、**[レポート]** ペイン内の最上位や最下位の数またはパーセントのみを表示します。<br /><br /> このオプションの詳細については、「[TopCount &#40;MDX&#41;](/sql/mdx/topcount-mdx)」、「[TopPercent &#40;MDX&#41;](/sql/mdx/toppercent-mdx)」、「[BottomCount &#40;MDX&#41;](/sql/mdx/bottomcount-mdx)」、および「[BottomPercent &#40;MDX&#41;](/sql/mdx/bottompercent-mdx)」を参照してください。|  
|**小計の表示 します。**|小計を表示します。|  
|**すべてのアイテムの合計**|すべてのメンバーに関する合計を **[レポート]** ペイン内に表示します。|  
|**空のセルの表示**|空のセルを **[レポート]** ペイン内に表示します。|  
|**結果をクリア**|**[レポート]** ペイン内の結果をクリアします。|  
|**コマンドおよびオプション**|**[コマンドおよびオプション]** ダイアログ ボックスを表示し、 **[レポート]** ペインで Microsoft Office 11.0 PivotTable コントロールの詳細プロパティを編集します。 **[コマンドおよびオプション]** ダイアログ ボックスの詳細については、Microsoft Office ドキュメントを参照してください。|  
|**パースペクティブ**|**[メタデータ]** ペインおよび **[レポート]** ペインで、データおよびメタデータを表示するパースペクティブを選択します。<br /><br /> パースペクティブを使用せずにキューブを表示するには、キューブ名を選択します。|  
|**言語**|**[メタデータ]** ペインおよび **[レポート]** ペインで、データおよびメタデータを表示する言語を選択します。<br /><br /> 既定の言語を使用してキューブを表示するには、 **[既定]** を選択します。|  
  
  