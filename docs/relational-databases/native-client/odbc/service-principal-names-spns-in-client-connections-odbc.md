---
title: クライアント接続 (ODBC) でのサービス プリンシパル名 (Spn)。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 1d60cb30-4c46-49b2-89ab-701e77a330a2
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 51bb287f23a407b7e09ddf433c3f9b31aafcbc03
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67913132"
---
# <a name="service-principal-names-spns-in-client-connections-odbc"></a>クライアント接続におけるサービス プリンシパル名 (SPN) (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ここでは、クライアント アプリケーションのサービス プリンシパル名 (SPN) をサポートする ODBC 属性および関数について説明します。 クライアント アプリケーションでの Spn の詳細についてを参照してください[サービス プリンシパル名&#40;SPN&#41;のクライアント接続のサポート](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)と[相互の Kerberos 認証を取得する](../../../relational-databases/native-client-odbc-how-to/get-mutual-kerberos-authentication.md)。  
  
## <a name="connection-string-keywords"></a>接続文字列キーワード  
 次の接続文字列キーワードを使用すると、クライアント アプリケーションは SPN を指定できます。  
  
|Keyword|[値]|  
|-------------|-----------|  
|**ServerSPN**|サーバーの SPN。 既定値は空文字です。この場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、ドライバーが生成した SPN を既定値として使用します。|  
|**FailoverPartnerSPN**|フェールオーバー パートナーの SPN。 既定値は空文字です。この場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、ドライバーが生成した SPN を既定値として使用します。|  
  
## <a name="connection-attributes"></a>接続属性  
 次の接続属性を使用すると、クライアント アプリケーションは、SPN を指定して認証方法を照会できます。  
  
|名前|型|使用方法|  
|----------|----------|-----------|  
|SQL_COPT_SS_SERVER_SPN<br /><br /> SQL_COPT_SS_FAILOVER_PARTNER_SPN|SQLTCHAR、読み取り/書き込み|サーバーの SPN を指定します。 既定値は空文字です。この場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、ドライバーが生成した SPN を既定値として使用します。<br /><br /> この属性を照会できるのは、属性がプログラムによって設定された後、または接続が開かれた後だけです。 接続が開いていない場合にこの属性を照会し、属性がプログラムによって設定されていない場合、SQL_ERROR が返され、"接続は開いていません" というメッセージで SQLState 08003 の診断レコードが記録されます。<br /><br /> 接続が開いている場合にこの属性を設定すると、SQL_ERROR が返され、"この操作は、ここでは実行できません" というメッセージで SQLState HY011 の診断レコードが記録されます。|  
|SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD|SQLTCHAR、読み取り専用|接続に使用された認証方法を返します。 アプリケーションに返される値は、Windows が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client に返す値です。 設定可能な値は、次のとおりです。<br /><br /> "NTLM"。これは NTLM 認証を使用して接続を開いたときに返されます。<br /><br /> "Kerberos"。これは Kerberos 認証を使用して接続を開いたときに返されます。<br /><br /> <br /><br /> この属性は、Windows 認証を使用する、開いている接続でのみ読み取りが可能です。 接続が開かれる前にこの属性を読み取ると、SQL_ERROR が返され、"接続は開いていません" というメッセージで SQLState 08003 がエラーとして記録されます。<br /><br /> この属性が Windows 認証を使用していない接続で照会されると、SQL_ERROR が返され、"属性またはオプション識別子が無効です (SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD は信頼関係接続でのみ使用できます)" というメッセージで SQLState HY092 がエラーとして記録されます。<br /><br /> 認証方法を特定できない場合は、SQL_ERROR が返され、"一般的なエラー" というメッセージで SQLState HY000 がエラーとして記録されます。|  
|SQL_COPT_SS_MUTUALLY_AUTHENTICATED|SQLSMALLINT、読み取り専用|接続されているサーバーが相互に認証された場合は SQL_TRUE を返します。それ以外の場合は SQL_FALSE を返します。<br /><br /> この属性は、開いている接続のみで読み取ることができます。 接続が開かれる前にこの属性を読み取ると、SQL_ERROR が返され、"接続は開いていません" というメッセージで SQLState 08003 がエラーとして記録されます。<br /><br /> Windows 認証を使用していない接続に対してこの属性が照会されると、SQL_FALSE が返されます。|  
  
## <a name="odbc-function-support-for-specifying-spns"></a>ODBC 関数による SPN 指定のサポート  
 次の ODBC 関数では、クライアント アプリケーションと SPN をサポートしています。  
  
-   [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
-   [SQLConnect](../../../relational-databases/native-client-odbc-api/sqlconnect.md)  
  
-   [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)  
  
-   [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)  
  
-   [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)  
  
## <a name="see-also"></a>関連項目  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
