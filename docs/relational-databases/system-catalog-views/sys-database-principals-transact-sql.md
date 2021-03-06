---
title: sys.database_principals (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_principals
- database_principals_TSQL
- sys.database_principals
- sys.database_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_principals catalog view
ms.assetid: 8cb239e9-eb8c-4109-9cec-0d35de95fa0e
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c369bfe81a86af7a11a370a4d827440cd4544a9d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022679"
---
# <a name="sysdatabaseprincipals-transact-sql"></a>sys.database_principals (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  それぞれのセキュリティの行でプリンシパルを返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|プリンシパルの名前。データベース内で一意です。|  
|**principal_id**|**int**|プリンシパルでは、データベース内で一意の ID。|  
|**type**|**char(1)**|プリンシパルの種類。<br /><br /> A = アプリケーション ロール<br /><br /> C = 証明書にマップされているユーザー<br /><br /> E = Azure Active Directory から外部ユーザー<br /><br /> G = Windows グループ<br /><br /> K = 非対称キーにマップされているユーザー<br /><br /> R = データベース ロール<br /><br /> S = SQL ユーザー<br /><br /> U = Windows ユーザー<br /><br /> X = Azure Active Directory グループまたはアプリケーションからの外部グループ|  
|**type_desc**|**nvarchar(60)**|プリンシパルの種類の説明です。<br /><br /> APPLICATION_ROLE<br /><br /> CERTIFICATE_MAPPED_USER<br /><br /> EXTERNAL_USER<br /><br /> WINDOWS_GROUP<br /><br /> ASYMMETRIC_KEY_MAPPED_USER<br /><br /> DATABASE_ROLE<br /><br /> SQL_USER<br /><br /> WINDOWS_USER<br /><br /> EXTERNAL_GROUPS|  
|**default_schema_name**|**sysname**|SQL 名でスキーマが指定されなかったときに使用される名前です。 プリンシパルの種類が S、U、または A. の場合は null|  
|**create_date**|**datetime**|プリンシパルが作成された日時。|  
|**modify_date**|**datetime**|プリンシパルが最後に変更された時刻。|  
|**owning_principal_id**|**int**|このプリンシパルを所有するプリンシパルの ID。 データベース ロール以外のすべてのプリンシパルが所有する必要があります**dbo**します。|  
|**sid**|**varbinary(85)**|プリンシパルの SID (セキュリティ識別子)。  SYS および INFORMATION SCHEMAS の場合は NULL です。|  
|**is_fixed_role**|**bit**|1 の場合、この行は、固定データベース ロールのいずれかのエントリを表します。 db_owner、db_accessadmin、db_datareader、db_datawriter、db_ddladmin、db_securityadmin、db_backupoperator、db_denydatareader、db_denydatawriter します。|  
|**authentication_type**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 認証の種類を示します。 使用可能な値とその説明を次に示します。<br /><br /> 0:認証なし<br />1:インスタンス認証<br />2:データベース認証<br />3:[Windows 認証]|  
|**authentication_type_desc**|**nvarchar(60)**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 認証の種類の説明です。 使用可能な値とその説明を次に示します。<br /><br /> NONE:認証なし<br />インスタンス:インスタンス認証<br />データベース:データベース認証<br />WINDOWS の場合:[Windows 認証]|  
|**default_language_name**|**sysname**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプリンシパルの既定の言語を示します。|  
|**default_language_lcid**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプリンシパルの既定の LCID を示します。|  
|**allow_encrypted_value_modifications**|**bit**|**適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]。<br /><br /> 一括コピー操作でのサーバーの暗号化メタデータ チェックを抑制します。 これにより、ユーザーがデータを復号化せず、テーブルまたはデータベース間で、Always Encrypted を使って暗号化データの一括コピーできます。 既定値は OFF です。 |      
  
## <a name="remarks"></a>コメント  
 *PasswordLastSetTime*プロパティは、SQL Server のサポートされているすべての構成で使用できますが、その他のプロパティは SQL Server が Windows Server 2003 またはそれ以降、CHECK_POLICY と CHECK_ の両方で実行されている場合にのみ使用できます有効期限が有効にします。 参照してください[パスワード ポリシー](../../relational-databases/security/password-policy.md)詳細についてはします。  
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーは自分のユーザー名、システム ユーザー、および固定データベース ロールを参照できます。 他のユーザーを参照するには、ALTER ANY USER、またはユーザーに対する権限が必要です。 ユーザー定義ロールを参照するには、ALTER ANY ROLE、またはロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-the-permissions-of-database-principals"></a>A:データベース プリンシパルのすべての権限を一覧表示  
 次のクエリは、明示的に許可または拒否するデータベース プリンシパルのアクセス許可を一覧表示します。  
  
> [!IMPORTANT]  
>  固定データベース ロールのアクセス許可は、sys.database_permissions には表示されません。 そのため、データベース プリンシパルには、この一覧にない追加のアクセス許可があります。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="b-listing-permissions-on-schema-objects-within-a-database"></a>B:データベース内のスキーマ オブジェクトの権限を一覧表示  
 次のクエリは、sys.database_principals と sys.database_permissions を sys.objects と sys.schemas に特定のスキーマ オブジェクトに付与または拒否リストのアクセス許可を結合します。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc,   
    pe.permission_name, s.name + '.' + o.name AS ObjectName  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id  
JOIN sys.objects AS o  
    ON pe.major_id = o.object_id  
JOIN sys.schemas AS s  
    ON o.schema_id = s.schema_id;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-listing-all-the-permissions-of-database-principals"></a>C: データベース プリンシパルのすべての権限を一覧表示  
 次のクエリは、明示的に許可または拒否するデータベース プリンシパルのアクセス許可を一覧表示します。  
  
> [!IMPORTANT]  
>  固定データベース ロールのアクセス許可に表示されない`sys.database_permissions`します。 そのため、データベース プリンシパルには、この一覧にない追加のアクセス許可があります。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="d-listing-permissions-on-schema-objects-within-a-database"></a>D:データベース内のスキーマ オブジェクトの権限を一覧表示  
 次のクエリの結合`sys.database_principals`と`sys.database_permissions`に`sys.objects`と`sys.schemas`特定のスキーマ オブジェクトに付与または拒否アクセス許可を一覧します。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc,   
    pe.permission_name, s.name + '.' + o.name AS ObjectName  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id  
JOIN sys.objects AS o  
    ON pe.major_id = o.object_id  
JOIN sys.schemas AS s  
    ON o.schema_id = s.schema_id;  
```  
  
## <a name="see-also"></a>関連項目  
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [包含データベース ユーザー - データベースの可搬](../../relational-databases/security/contained-database-users-making-your-database-portable.md)   
 [Azure Active Directory の認証を使用して、SQL データベースに接続します。](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)  
  
  


