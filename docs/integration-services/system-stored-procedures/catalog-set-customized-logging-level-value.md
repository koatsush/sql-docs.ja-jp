---
title: catalog.set_customized_logging_level_value | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: d83fb763-c7c6-4e20-bd10-0f995598b198
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 0146d58a1495ad5c17625edbb9b9c6f2d295cfb8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985305"
---
# <a name="catalogsetcustomizedlogginglevelvalue"></a>catalog.set_customized_logging_level_value 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  統計情報、または既存のログ記録のカスタマイズされたレベルで記録されたイベントを変更します。 カスタマイズされたログ記録レベルの詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_customized_logging_level_value [ @level_name = ] level_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>引数  
 [ @level_name = ] *level_name*  
 既存の名前は、ログ記録レベルをカスタマイズします。  
  
 *level_name* は **nvarchar(128)** です。  
  
 [ @property_name = ] *property_name*  
 変更するプロパティの名前。 有効な値は **PROFILE** と **EVENTS**です。  
  
 *Property_name* は **nvarchar(128)** です。  
  
 [ @property_value = ] *property_value*  
 指定した指定したプロパティの新しい値では、ログ記録レベルをカスタマイズします。  
  
 プロファイルとイベントの有効な値の一覧は、「[catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md)」を参照してください。  
  
 *property_value* は **bigint** です。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   ユーザーには、必要なアクセス許可がありません。  
  
  
