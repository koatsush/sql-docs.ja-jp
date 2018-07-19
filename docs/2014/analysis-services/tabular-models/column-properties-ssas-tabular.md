---
title: 列のプロパティ (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.columnprop.f1
ms.assetid: 4046c1a3-46c7-47db-b355-52e9c2f23671
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 437f225da3d771298a0fcf7af864a45953b194be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169303"
---
# <a name="column-properties-ssas-tabular"></a>Column Properties (SSAS Tabular)
  このトピックでは、テーブル モデルの列のプロパティについて説明します。  
  
 このトピックのセクション:  
  
-   [列のプロパティ](#bkmk_properties)  
  
-   [列プロパティの設定を構成するには](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> 列のプロパティ  
 **基本**  
  
|プロパティ|既定の設定|説明|  
|--------------|---------------------|-----------------|  
|**列名**||モデルに格納され、レポート クライアントのフィールドの一覧に表示される列の名前。|  
|**データ形式**|インポート時に自動的に決定します。|この列のデータに使用される表示形式を指定します。 データ形式を定義したら、各形式に固有のプロパティを設定できます。 たとえば、 **[通貨]** 形式を選択した場合は、表示される小数点以下の桁数の設定、桁区切り記号の選択、および通貨記号の選択を行います。 このプロパティには、次のオプションがあります。<br /><br /> **全般**<br /><br /> **10 進数**<br /><br /> **整数**<br /><br /> **Currency**<br /><br /> **[パーセント]**<br /><br /> **[指数]**<br /><br /> 列の値に画像が含まれる場合は、「 **基本画像**」を参照してください。|  
|**[データ型]**|インポート時に自動的に決定します。|列のすべての値のデータ型を指定します。|  
|**[説明]**||列の説明文です。<br /><br /> 特定のレポート クライアントで、フィールド一覧のこの列にエンド ユーザーがカーソルを重ねると、ツールヒントとしてこの説明が表示されます。|  
|**[非表示]**|False|レポート クライアント フィールドの一覧で、列を非表示にするかどうかを指定します。<br /><br /> このプロパティを **[True]** に設定すると、この列は非表示になります。 たとえば、識別子またはキーを含む列は、通常はエンド ユーザーにとっては役に立ちません。<br /><br /> レポート クライアントで列を非表示にしても、そのフィールドはモデル データでは非表示にはなりません。 モデルに対するクエリを作成すると、そのフィールドが表示されます。 非表示の列は、引き続きグループ化または並べ替えに使用できます。<br /><br /> **[非表示]** プロパティは、データ セキュリティはまったく考慮されません。 データのセキュリティを確保するため、"ロール" では行フィルターを使用してください。 詳しくは、「[ロール &#40;SSAS テーブル&#41;](roles-ssas-tabular.md)」をご覧ください。|  
|**列で並べ替え**||この列の値を並べ替えるために使用するもう 1 つの列を指定します。 2 つの列の間にリレーションシップが存在する必要があります。<br /><br /> この値には、既存の列の名前を指定してください。 数式またはメジャーを指定することはできません。|  
  
 **レポートのプロパティ**  
  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] テーブル動作プロパティの設定の詳細については、「[Power View レポートのテーブル動作プロパティの構成 (SSAS テーブル)](power-view-configure-table-behavior-properties-for-reports.md)」を参照してください。  
  
|プロパティ|既定の設定|説明|  
|--------------|---------------------|-----------------|  
|[既定の画像]|False|行データを表す画像を提供する列 (たとえば、従業員レコードの写真 ID) を指定します。|  
|既定のラベル|False|行データを表す表示名を提供する列 (たとえば、従業員レコードの従業員名) を指定します。|  
|[画像の URL]/[データ カテゴリ] (SP1)|False|サーバー上の画像へのハイパーリンクとして、この列の値を指定します。 たとえば、「 http://localhost/images/image1.jpg」のように入力します。|  
|[一意の行を保持]|False|重複している場合でも一意として扱う必要のある値を提供する列を指定します (たとえば、2 人以上の従業員が同じ名前を持つ可能性がある場合の従業員の姓名)。|  
|[行識別子 (ROWID)]|False|一意の値のみ含む列を指定します。その列を内部グループ化キーとして使用できます。|  
|集計の方法|既定|この列がフィールドの一覧に追加されたとき、列の計算に集計関数 SUM を適用するレポート クライアント ツールを指定します。 既定の計算を変更するには、ドロップダウン リストから選択します。 このプロパティは、集計が可能な種類の列にのみ適用されます。|  
|[テーブルの詳細の位置]|[既定のフィールド セットがありません]|レポート クライアントでテーブルが見やすくなるように、1 つのテーブルのフィールド セットに追加できる、この列またはメジャーを指定します。|  
  
###  <a name="bkmk_config_prop"></a> 列プロパティの設定を構成するには  
  
1.  モデル デザイナーでテーブルから列を選択します。  
  
2.  **[プロパティ]** ウィンドウで、プロパティをクリックして値を入力するか、下矢印をクリックして設定オプションを選択します。  
  
## <a name="see-also"></a>参照  
 [レポートのプロパティを表示する power &#40;SSAS 表形式&#41;](properties-ssas-tabular.md)   
 [非表示にするか、列を固定&#40;SSAS 表形式&#41;](hide-or-freeze-columns-ssas-tabular.md)   
 [テーブルに列を追加&#40;SSAS 表形式&#41;](add-columns-to-a-table-ssas-tabular.md)  
  
  