---
title: テーブル値パラメーターのデータ変換およびその他のエラーと警告 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a4abc28204df04ec77ee6b22e3c7a0c08c832bcd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129146"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>テーブル値パラメーターのデータ変換およびその他のエラーと警告
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  テーブル値パラメーターの列の値は、他の列やパラメーターの値と同じ方法で、クライアントのデータ型とサーバーのデータ型間で変換できます。 ただし、テーブル値パラメーターには複数の列と複数の行を含めることができるため、エラーが発生した箇所の実際の値を識別できることが重要です。  
  
 テーブル値パラメーターの列でエラーまたは警告が検出された場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client によって診断レコードが生成されます。 エラー メッセージには、テーブル値パラメーターのパラメーター番号に加え、列序数と行番号が含まれます。 アプリケーションでは、診断レコード内の SQL_DIAG_SS_TABLE_COLUMN_NUMBER および SQL_DIAG_SS_TABLE_ROW_NUMBER という診断フィールドを使用して、エラーと警告に関連付けられている値を特定することもできます。 これらの診断フィールドは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンで使用できます。  
  
 診断レコードの SQLSTATE コンポーネントとメッセージ コンポーネントは、他のすべての点で既存の ODBC の動作に準拠しています。 つまり、を除き、パラメーター、行、および列の識別情報、エラー メッセージがあるテーブル値パラメーターの値は同じ非テーブル値パラメーターの場合とします。  
  
## <a name="see-also"></a>関連項目  
 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
