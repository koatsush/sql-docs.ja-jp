---
title: トレース定義の既定値の設定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], defaults
ms.assetid: ab9fc570-797d-411e-814f-1c46d2d5feae
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5682d9234ea84fad3a55c8d601beb29a7de38f64
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208372"
---
# <a name="set-trace-definition-defaults-sql-server-profiler"></a>トレース定義の既定値の設定 (SQL Server Profiler)
  トレース定義の既定値は、プロバイダーまたはサーバーごとに使用される既定のトレース テンプレートです。 既定のトレース テンプレートは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に設定できます。  
  
### <a name="to-set-trace-definition-defaults"></a>トレース定義の既定値を設定するには  
  
1.  **[ファイル]** メニューの **[テンプレート]** をクリックし、 **[テンプレートの編集] をクリックします。**  
  
2.  **[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[全般]** タブで、 **[サーバーの種類の選択]** ボックスの一覧からサーバーの種類を選択します。  
  
3.  **[テンプレート名の選択]** ボックスの一覧で、トレース定義の既定値として使用するテンプレートの名前を選択します。  
  
4.  **[選択したサーバーの種類に対する既定のテンプレートとして使用する]** チェック ボックスをオンにします。  
  
5.  必要な場合は、 **[イベントの選択]** タブをクリックして、テンプレートを編集します。  
  
6.  **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler のテンプレート](sql-server-profiler-templates.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  