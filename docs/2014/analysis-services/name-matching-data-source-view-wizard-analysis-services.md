---
title: 名前を一致する (データ ソース ビュー ウィザード) (Analysis Services) |Microsoft Docs
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
- sql12.asvs.datasourceviewwizard.namematchingcriteria.f1
ms.assetid: 7f811e02-0fe6-45c9-a7b7-29c61032d96b
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 258b23cc260ea4d31296aa00964138df399da516
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155383"
---
# <a name="name-matching-data-source-view-wizard-analysis-services"></a>[名前の一致] (データ ソース ビュー ウィザード) (Analysis Services)
  **[名前の一致]** ページを使用すると、データ ソース ビューに対して選択したテーブルと、スキーマ内の他のテーブルとの間で可能なリレーションシップを検出するための基準を選択できます。 これらのテーブルの間に物理的な外部キー リレーションシップが存在しない場合は、この条件は、関連テーブルを識別してデータ ソース ビューに追加するときに役に立ちます。 また、名前の一致によって識別される論理リレーションシップもデータ ソース ビューに追加されます。  
  
> [!NOTE]  
>  このページは、複数のテーブルを持ち、テーブル間に外部キー リレーションシップがないデータ ソースを選択した場合にのみ表示されます。  
  
## <a name="options"></a>および  
 **列を照合することによって、論理リレーションシップを作成します。**  
 オンにした場合、データ ソース ビューに含めるテーブルと、スキーマ内の他のテーブルとの間で可能な論理的依存関係およびリレーションシップを検出するために、名前の一致条件が使用されます。 このチェック ボックスをオフにすると、データ ソース内のテーブル間の論理リレーションシップを識別する際に名前の一致条件は使用されません。  
  
 **外部キーを一致します。**  
 データ ソース内のテーブルおよびビューの間に論理リレーションシップを作成するために使用する条件を選択します。 文字列の照合において、英数字以外の文字は無視されます。 たとえば、"Customer ID"、"Customer_ID"、"CustomerID" はすべて一致します。 次の表に示すいずれかのオプションを選択すると、特定の条件下でリレーションシップを作成できます。  
  
|Select|作成されるリレーションシップ|  
|------------|---------------|  
|**[主キーと同一の名前]**|選択されたテーブルの主キー列の名前に一致する列名を持つ、任意のテーブルへの論理リレーションシップ。|  
|**[対象のテーブル名と同一の名前]**|選択されたテーブルの名前に一致する列名を持つ、任意のテーブルへの論理リレーションシップ。|  
|**一致先のテーブル名と主キー名の組み合わせ**|"選択されたテーブルの名前" と "選択されたテーブルの主キー列の名前" を連結した名前に一致する列名を持つ、任意のテーブルへの論理リレーションシップ。 連結した名前において、英数字以外の文字は無視されます。たとえば、"Product ID"、"Product_ID"、"ProductID" はすべて一致します。|  
  
 **説明とサンプル**  
 選択された条件の説明とサンプルを表示します。  
  
  