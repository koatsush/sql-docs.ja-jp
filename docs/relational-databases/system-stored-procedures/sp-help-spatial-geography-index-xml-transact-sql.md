---
title: sp_help_spatial_geography_index_xml (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index_xml_TSQL
- sp_help_spatial_geography_index_xml
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index_xml procedure
ms.assetid: 821d4127-3ce5-4474-8561-043404a20d81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dce44e2045b7d3031058ffd976b01bdd53801c48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085140"
---
# <a name="sphelpspatialgeographyindexxml-transact-sql"></a>sp_help_spatial_geography_index_xml (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  に関する名前と指定した一連のプロパティの値を返します、 **geography**空間インデックスです。 プロパティまたはインデックスのすべてのプロパティのコア セットを返すことができます。  
  
 結果は、選択したプロパティの名前と値を表示する XML フラグメントで返されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_spatial_geography_index_xml [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>引数  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)します。  
  
## <a name="properties"></a>Properties  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーには、プロシージャにアクセスするための PUBLIC ロールを割り当てる必要があります。 サーバーとオブジェクトの読み取りアクセス許可が必要です。  
  
## <a name="remarks"></a>コメント  
 NULL 値を含むプロパティは、返されるセットに含まれません。  
  
## <a name="example"></a>例  
 次の例では`sp_help_spatial_geography_index_xml`空間インデックスを調査する**SIndx_SpatialTable_geography_col2**テーブルで定義された**geography_col**で指定されたクエリ サンプルの **@qs** . この例では、選択したプロパティの値と名前を表示する XML フラグメントで指定したインデックスの主要プロパティを返します。  
  
 [XQuery](../../xquery/xquery-basics.md)結果セットに、特定のプロパティを返すことが実行されます。  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
declare @x xml;  
exec sp_help_spatial_geography_index_xml 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs, @x output;  
select @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 ような[sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)、このストアド プロシージャのプロパティに簡単にプログラムによるアクセスを提供します、 **geography**空間インデックスおよび XML の結果セットをレポートします。  
  
 境界ボックス、 **geography**は地球全体です。  
  
## <a name="requirements"></a>必要条件  
  
## <a name="see-also"></a>関連項目  
 [空間インデックス ストアド プロシージャ](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [XQuery の基礎](../../xquery/xquery-basics.md)   
 [XQuery 言語リファレンス](../../xquery/xquery-language-reference-sql-server.md)  
  
  
