---
title: コマンド ウィンドウ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1ec8bc61454647bd553fa73513a1b06b71edc85b
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701210"
---
# <a name="transact-sql-debugger---command-window"></a>Transact-SQL デバッガー - [コマンド] ウィンドウ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  **[コマンド]** ウィンドウを使用すると、現在デバッグ中の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディター ウィンドウのコードに対してデバッグ コマンドや編集コマンドなどのコマンドを実行できます。 **[コマンド]** ウィンドウを使用するには、デバッグ モードである必要があります。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **[コマンド]** ウィンドウでもサポートされているコマンドの多くをサポートしています。 詳細については、 [Visual Studio のコマンド ウィンドウに関するページ](https://go.microsoft.com/fwlink/?LinkId=112007)を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **[コマンド] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
 **変数の値を出力するには**  
  
-   **[コマンド] ウィンドウ**で、「**Debug.Print \<変数名>**」と入力し、Enter キーを押します。  
  
 **現在のスレッドに関する情報を一覧表示するには**  
  
-   **[コマンド]** ウィンドウで、「 **Debug.ListThread**」と入力し、Enter キーを押します。  
  
 **[クイック ウォッチ] ウィンドウに変数を追加するには**  
  
-   **[コマンド] ウィンドウ**で、「**Debug.QuickWatch \<変数名>**」と入力し、Enter キーを押します。  
  
## <a name="see-also"></a>参照  
 [Transact-SQL デバッガー](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  