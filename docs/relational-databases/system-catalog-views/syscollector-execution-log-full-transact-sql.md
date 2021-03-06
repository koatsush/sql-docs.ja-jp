---
title: syscollector_execution_log_full (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_log_full
- syscollector_execution_log_full_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_execution_log_full view
ms.assetid: 6c8db22d-2e4c-4b7c-ac5a-8762ef1b175b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4bcbbf3d4e0e0b77156b7adceedbdc5aad97afdc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060363"
---
# <a name="syscollectorexecutionlogfull-transact-sql"></a>syscollector_execution_log_full (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  実行ログがいっぱいになったときは、コレクション セットまたはパッケージに関する情報を提供します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|log_id|**bigint**|各コレクション セットの実行を識別します。 このビューを他の詳細なログを結合するために使用します。 NULL 値が許可されます。|  
|parent_log_id|**bigint**|親パッケージまたはコレクション セットを識別します。 NULL 値は許可されません。 Id はどのパッケージがどのコレクションによって開始されたかを判断することができます、親子関係としてチェーン化を設定します。 このビューは、ログ エントリをその親と子リンケージでグループ化され、呼び出しチェーンが明確に表示されるよう、パッケージの名前にインデントを設定します。|  
|NAME|**nvarchar (4000)**|コレクション セットまたはこのログ エントリを表すパッケージの名前。 NULL 値が許可されます。|  
|status|**smallint**|コレクション セットまたはパッケージの現在の状態を示します。 NULL 値が許可されます。<br /><br /> 値は次のとおりです。<br /><br /> 0 = 実行中<br /><br /> 1 = が完了しました<br /><br /> 2 = 失敗|  
|runtime_execution_mode|**smallint**|コレクション セットのアクティビティがデータを収集するか、データをアップロードするかどうかを示します。 NULL 値が許可されます。|  
|start_time|**datetime**|コレクション セットまたはパッケージが開始された時刻。 NULL 値が許可されます。|  
|last_iteration_time|**datetime**|継続的には、前回のパッケージにスナップショットがキャプチャされる、パッケージを実行しています。 NULL 値が許可されます。|  
|finish_time|**datetime**|完成したパッケージおよびコレクションが完了する実行設定の時間です。 NULL 値が許可されます。|  
|duration|**int**|パッケージまたはコレクション セットが実行されているを秒単位での時刻。 NULL 値が許可されます。|  
|failure_message|**nvarchar(2048)**|コレクション セットまたはパッケージが失敗した場合、最新のエラーは、そのコンポーネントのメッセージします。 NULL 値が許可されます。 詳細なエラー情報を取得する、 [fn_syscollector_get_execution_details &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md)関数。|  
|演算子 (operator)|**nvarchar(128)**|コレクション セットまたはパッケージを開始したユーザーを識別します。 NULL 値が許可されます。|  
|package_execution_id|**uniqueidentifier**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] ログ テーブルへのリンクを提供します。 NULL 値が許可されます。|  
|collection_set_id|**int**|Msdb 内のデータ コレクション構成テーブルへのリンクを提供します。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 SELECT 権限が必要**dc_operator**します。  
  
## <a name="see-also"></a>関連項目  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
