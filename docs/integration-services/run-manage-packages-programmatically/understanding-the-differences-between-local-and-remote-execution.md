---
title: ローカル実行とリモート実行の相違点について | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 61233900def55fc28627869a134bddaf786f5548
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028442"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>ローカル実行とリモート実行の相違点について

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  パッケージの開発者および管理者は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行場所に関連する制限があることを知っておく必要があります。  
  
-   **パッケージは、パッケージを起動するプログラムと同じコンピューターで実行されます**。 プログラムが別のサーバー上にリモートに格納されたパッケージを読み込む場合であっても、そのパッケージはローカル コンピューターで実行されます。  
  
-   **パッケージを開発環境の外部で実行することができるのは、そのコンピューターに Integration Services がインストールされている場合のみです**。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] がインストールされていないクライアント コンピューターでは、パッケージを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の外部で実行することはできません。また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ライセンスの条項により、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を他のコンピューターにインストールすることは許可されない場合があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はサーバー コンポーネントであるため、クライアント コンピューターに再配布できません。 クライアント コンピューターからパッケージを実行するには、パッケージが確実にサーバー上で実行される方法で、パッケージを起動する必要があります。  
  
 保存済みパッケージの読み込みと実行の詳細については、次のトピックを参照してください。  
  
-   [プログラムによるローカル パッケージの読み込みと実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [プログラムによるリモート パッケージの読み込みと実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 保存済みパッケージの実行と、その出力のカスタム プログラムへの読み込みの詳細については、次のトピックを参照してください。  
  
-   [ローカル パッケージの出力の読み込み](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
## <a name="see-also"></a>参照  
 [プログラムによるローカル パッケージの読み込みと実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [プログラムによるリモート パッケージの読み込みと実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [ローカル パッケージの出力の読み込み](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
