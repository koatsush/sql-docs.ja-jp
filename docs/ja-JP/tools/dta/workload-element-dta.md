---
title: Workload 要素 (DTA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f39cc50aa258df595bd7c010d992740a0a68976
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="workload-element-dta"></a>Workload 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] チューニング セッションで使用するワークロードを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**DTAInput** 要素につき 1 回使用できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|**子要素**|[File 要素 &#40;DTA&#41;](../../tools/dta/file-element-dta.md)<br /><br /> [Workload の Database 要素 &#40;DTA&#41;](../../tools/dta/database-element-for-workload-dta.md)<br /><br /> [EventString 要素 &#40;DTA&#41;](../../tools/dta/eventstring-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 ワークロードとは、チューニングするデータベースに対して実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのセットです。 データベース エンジン チューニング アドバイザーは、ワークロードとして [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、トレース ファイル、およびトレース テーブルを使用できます。  
  
 XML 入力ファイルでワークロードを指定し、 **dta** ツールを使用してコマンド ラインでもワークロードを指定した場合、コマンド ラインで指定したワークロードがチューニングに使用されます。 コマンド ラインで指定したチューニング オプションはすべて、XML 入力ファイルで指定したオプションより優先されます。 唯一の例外は、ユーザー定義の構成が XML 入力ファイルに評価モードで入力されている場合だけです。 たとえば、XML 入力ファイルの **Configuration** 要素に構成が入力されており、 **EvaluateConfiguration** 要素も同様にチューニング オプションの 1 つとして指定されている場合、XML 入力ファイルで指定されたチューニング オプションは、コマンド プロンプトから入力されるいずれのチューニング オプションよりも優先されます。  
  
 各チューニング セッションには 1 つのワークロードを指定する必要があります。  
  
## <a name="example"></a>例  
 次のコード例では、 **Workload** 要素に対して **MyDatabase.MyDBOwner.TuningTable001** トレース テーブルを指定します。 **TuningTable001** は SQL Server Profiler でチューニング テンプレートを使用し、トレース出力をテーブルとして保存することによって作成されたものです。  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  