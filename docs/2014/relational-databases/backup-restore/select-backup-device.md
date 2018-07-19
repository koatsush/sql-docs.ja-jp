---
title: '[バックアップ デバイスの選択] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: aeecd5db3b5c8666eb7e585dbacc522da26f0c44
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290938"
---
# <a name="select-backup-device"></a>[バックアップ デバイスの選択]
  **[バックアップ デバイスの選択]** ダイアログ ボックスを使用すると、復元操作で使用する論理バックアップ デバイスを選択できます。  
  
 論理バックアップ デバイスは、オペレーティング システムによって提供される物理デバイス (テープ ドライブまたはディスク ドライブ) に対応するユーザー定義の論理デバイスです。  
  
> [!NOTE]  
>  バックアップで複数のバックアップ デバイスを使用する場合、すべてのバックアップ デバイスが 1 つの種類のデバイスに対応する必要があります。  
  
 **SQL Server Management Studio を使用してバックアップ デバイスの内容を表示するには**  
  
-   [バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>および  
 **バックアップ デバイス**  
 復元操作で使用する論理バックアップ デバイスの名前を、このリスト ボックスから選択します。  
  
 バックアップデバイスのコンテンツの表示方法の詳細については、「 [論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)」を参照してください。  
  
## <a name="remarks"></a>コメント  
 探していたバックアップを含む論理バックアップ デバイスが一覧に表示されない場合、バックアップが 1 つ以上のファイルまたはテープ ドライブに直接書き込まれている可能性があります。 この場合、 **[バックアップ デバイスの選択]** ダイアログ ボックスを取り消し、 **[バックアップの指定]** ダイアログ ボックスの **[バックアップ メディア]** ボックスで **[ファイル]** または **[テープ]** を選択します。  
  
## <a name="see-also"></a>参照  
 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  