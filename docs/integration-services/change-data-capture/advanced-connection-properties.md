---
title: 高度な接続プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: janinezhang
ms.author: janinez
ms.openlocfilehash: a6d17e67b5f4b48f20752e84300dc8c993a67d1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074656"
---
# <a name="advanced-connection-properties"></a>高度な接続プロパティ

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  **[高度な接続プロパティ]** ダイアログ ボックスを使用すると、接続文字列に接続パラメーターをさらに追加できます。  
  
 追加の接続パラメーターには、使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース インスタンスでサポートされる任意の ODBC 接続パラメーターを使用できます。  
  
 **[高度な接続プロパティ]** ダイアログ ボックスを使用して追加したパラメーターは、 **[SQL Server への接続]** ダイアログ ボックスで選択したパラメーターに追加されます。  
  
 指定した各パラメーターの最後のインスタンスは、そのパラメーターの前のインスタンスをオーバーライドします。 **[高度な接続パラメーター]** ダイアログ ボックスを使用して追加したパラメーターは、 **[SQL Server 接続]** ダイアログ ボックスで指定したパラメーターの後に続き、それらのパラメーターを置換します。 たとえば、 **[SQL Server 接続]** ダイアログ ボックスの [サーバー名] で「SERVER1」と指定し、 **[追加の接続パラメーター]** ページで「;SERVER=SERVER2」と指定した場合、SERVER2 に接続されます。  
  
 **[高度な接続プロパティ]** ダイアログ ボックスを使用して追加したパラメーターは、プレーンテキストとして渡されます。  
  
> [!IMPORTANT]  
>  **[高度な接続プロパティ]** ダイアログ ボックスにはログイン資格情報を含めないでください。 このダイアログ ボックスで指定したパラメーターは、ネットワーク経由で渡されるときに暗号化されません。  
  
## <a name="see-also"></a>参照  
 [CDC デザイナー コンソールへのアクセス](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [インスタンスの作成のための SQL サーバー接続](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  
