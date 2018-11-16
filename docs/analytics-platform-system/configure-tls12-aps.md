---
title: 'Analytics Platform System での TLS 1.2 の構成 |Microsoft Docs '
description: APS で TLS 1.2 を構成する推奨事項
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 638633a84721532ad05a52126aa7bcfd3f2bb6b7
ms.sourcegitcommit: 3e1efbe460723f9ca0a8f1d5a0e4a66f031875aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2018
ms.locfileid: "50237182"
---
# <a name="configure-tls-12-in-aps"></a>AP で TLS 1.2 を構成します。

TLS 1.2 のみを使用するアクセス ポイントをセキュリティで保護するには、すべての物理および仮想ホストでは、その他のプロトコルを明示的に無効にする必要があります。 プロトコルを無効にするには、レジストリ設定の変更が必要です。

> [!WARNING]
> ここでは、レジストリの変更方法を示す手順について説明します。 ただし、深刻な問題は、レジストリが正しくないデータの損失が発生し、オペレーティング システムの再インストールする必要がありますを変更する場合に発生する可能性があります。 強くお勧め、レジストリのバックアップを変更する前にします。 バックアップがあれば、問題が発生してもレジストリを復元できます。 バックアップし、レジストリを復元する方法の詳細については、以下の記事では、マイクロソフト サポート技術情報番号をクリックします。<br>
[322756](https://support.microsoft.com/en-us/help/322756)バックアップし、Windows でレジストリを復元する方法

**無効にします。**
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
```

次にキーを設定、クライアント マシン AP SSIS 変換先アダプターなどのツールがインストールされています。
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```


