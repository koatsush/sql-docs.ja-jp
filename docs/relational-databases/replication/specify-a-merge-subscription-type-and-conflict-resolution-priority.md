---
title: マージ サブスクリプションの種類と競合解決の優先度を指定する | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0fe64a74b85aca2ff02308c384dce89b9be540a1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67907608"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>マージ サブスクリプションの種類と競合解決の優先度を指定する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  サブスクリプションの新規作成ウィザードの **[サブスクリプションの種類]** ページで、マージ サブスクリプションの種類と競合解決の優先度を指定します。 このウィザードの使用方法の詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) 」および「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」を参照してください。  
  
 サブスクリプションの種類はサブスクリプションの作成後には変更できませんが、サーバー サブスクリプションの種類の優先度は、 **[サブスクリプションのプロパティ - \<Publisher>: \<PublicationDatabase>]** ダイアログ ボックスで変更できます。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) 」および「 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>マージ サブスクリプションの種類と競合解決の優先度を指定するには  
  
1.  サブスクリプションの新規作成ウィザードの **[サブスクリプションの種類]** ページで、 **[サブスクリプションの種類]** オプションに対して **[クライアント]** または **[サーバー]** を選択します。  
  
2.  サブスクリプションの種類として **[サーバー]** を選択した場合は、 **[競合解決の優先度]** オプションの値 (0.00 ～ 99.99) も入力します。  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>競合解決の優先度を変更するには  
  
1.  **サブスクリプションのプロパティ - \<パブリッシャー>:\<PublicationDatabase>** (パブリッシャー) で、**優先度** オプションの値 (0.00 から 99.99) を入力します。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
