---
title: スキーマのキャッシュ (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d4ac7ee9c119daa4f1aa41c1485aae57ee280c5f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093290"
---
# <a name="schema-caching-sqlxml-40"></a>スキーマのキャッシュ (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Microsoft SQL Server 2000 Web Release 1、Microsoft SQLXML 2.0、および SQLXML 3.0 の XML のサイド バイ サイドでインストール、すべてのバージョンでのキャッシュは、次のレジストリ キーを使用してスキーマを明示的に制御できます。  
  
 Web Release 1:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 サイド バイ サイドでインストールの詳細については、次を参照してください。 [SQLXML 4.0 SP1 の新](../../../relational-databases/sqlxml/what-s-new-in-sqlxml-4-0-sp1.md)します。  
  
 スキーマをキャッシュすると、XPath クエリのパフォーマンスが大きく向上します。 マッピング スキーマに対して XPath クエリを実行すると、スキーマはメモリに格納され、必要なデータ構造がメモリ内で作成されます。 スキーマのキャッシュを設定している場合、スキーマはメモリに残るので、以降の XPath クエリのパフォーマンスが向上します。  
  
 スキーマのキャッシュ サイズは、レジストリに上のキーを追加することで設定できます。  
  
 スキーマ サイズは、使用可能なメモリ量と、使用しているスキーマ数に基づいて設定します。 既定の**SchemaCacheSize**サイズは 31 です。 設定した場合**SchemaCacheSize**高くより多くのメモリが使用されます。 スキーマのアクセスが遅い場合はキャッシュ サイズを増やし、メモリが少ない場合はキャッシュ サイズを減らします。  
  
 パフォーマンス上の理由をお勧め設定する**SchemaCacheSize**通常使用するスキーマのマッピングの数より大きい。 場合、スキーマの数を増やすと**SchemaCacheSize**が小さいするスキーマの数よりパフォーマンスが低下します。  
  
> [!NOTE]  
>  スキーマへの変更は約 2 分経たないとキャッシュに反映されないため、開発時はスキーマをキャッシュしないことをお勧めします。  
  
## <a name="see-also"></a>参照  
 [テンプレートのキャッシュ&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [XSL のキャッシュ&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
