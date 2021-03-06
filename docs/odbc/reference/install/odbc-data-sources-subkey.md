---
title: ODBC データ ソースのサブキー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a1d0c506c4a4b33d7138378032947821d4e9f3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093992"
---
# <a name="odbc-data-sources-subkey"></a>ODBC データ ソースのサブキー
ODBC データ ソースのサブキーの下の値は、データ ソースを一覧表示します。 これらの値の形式は、次の表に示すようにします。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|*data-source-name*|REG_SZ|*ドライバーの説明*|  
  
 *データのソース名*(通常は、ユーザーを要求) を管理プログラムによって値が定義されていると*ドライバー説明*ドライバー開発者によって定義されます (の名前では、通常は、DBMS ドライバーに関連付けられている)。  
  
 たとえば、3 つのデータ ソースが定義されているとします。インベントリは、SQL Server を使用します。給与支払い名簿 dBASE; を使用します。スタッフ、書式設定されたテキスト ファイルを使用します。 ODBC データ ソースのサブキーの下の値が次のようにあります。  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
