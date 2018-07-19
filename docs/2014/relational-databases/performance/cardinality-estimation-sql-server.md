---
title: カーディナリティ推定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 11/24/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 81f9d8c849622a622631bc8153dc7d4cffc7d258
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251884"
---
# <a name="cardinality-estimation-sql-server"></a>カーディナリティ推定 (SQL Server)
  カーディナリティ推定機能と呼ばれる、カーディナリティ推定ロジックがで再設計された[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]クエリ プランの品質を向上させるためクエリのパフォーマンスを向上させるためにします。 新しいカーディナリティ推定機能には、現在の OLTP ワークロードとデータ ウェアハウス ワークロードで適切に機能する想定とアルゴリズムが組み込まれています。 この機能は、現在のワークロードを対象とするカーディナリティ推定に関する詳細な調査、および SQL Server のカーディナリティ推定機能を向上させるための過去 15 年にわたる研究を土台としています。 お客様からのフィードバックによると、大半のクエリは今回の変更によって性能が向上するか、何も変化しないこと、一方で、少数のクエリは以前のカーディナリティ推定機能と比較すると性能が低下する可能性があることが示されています。  
  
> [!NOTE]  
>  カーディナリティ推定とは、クエリの結果に含まれる行の数を予測することです。 クエリ オプティマイザーはこれらの推定を使用して、クエリを実行するプランを選択します。 クエリ プランの品質は、クエリ パフォーマンスの向上に直接的な影響を及ぼします。  
  
## <a name="performance-testing-and-tuning-recommendations"></a>パフォーマンス テストとチューニングに関する推奨事項  
 新しいカーディナリティ推定機能は、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] を使用して作成したすべての新しいデータベースで有効になっています。 ただし、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] にアップグレードするだけでは、既存のデータベースでは新しいカーディナリティ推定機能は有効になりません。  
  
 実稼動システムで新しいカーディナリティ推定機能を有効にする前に、最適なクエリ パフォーマンスが達成できることを確認するために、次の推奨事項を使用して実際のワークロードをテストしてください。  
  
1.  新しいカーディナリティ推定機能を使用するように、すべての既存のデータベースをアップグレードします。 これを行うには、次のように使用します。 [ALTER DATABASE 互換性レベル&#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)データベースの互換性レベルを 120 に設定します。  
  
2.  新しいカーディナリティ推定機能を使用してテスト ワークロードを実行し、パフォーマンス上の問題に対してトラブルシューティングを現在実行しているのと同じ方法で、パフォーマンスの新しい問題に対するトラブルシューティングを実行します。  
  
3.  トレース フラグ 9481で使用される、カーディナリティ推定機能のバージョンを使用すると、クエリを実行するには、ワークロードが新しいカーディナリティ推定機能(データベース互換性レベル120(SQLServer2014))使用して実行し、特定のクエリが低下した、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以前のバージョン。 トレース フラグを指定してクエリを実行するには、サポート技術情報の資料「 [特定のクエリ レベルに対応するさまざまなトレース フラグを使用して制御できる、プランが影響を及ぼす SQL Server クエリ オプティマイザーの動作の有効化](http://support.microsoft.com/kb/2801413)」を参照してください。  
  
4.  すべての新しいカーディナリティ推定機能を使用するには、一度にデータベースを変更した場合のすべてのデータベースの以前のカーディナリティ推定機能を使用を使用して[ALTER DATABASE 互換性レベル&#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)にデータベースの互換性レベルを 110 に設定します。  
  
5.  データベース互換性レベル 110 を使用してワークロードを実行し、新しいカーディナリティ推定機能を使用して特定のクエリをテストまたは実行しようとする場合は、SQL Server 2014 バージョンのカーディナリティ推定機能を使用するために、トレース フラグ 2312 を指定してそのクエリを実行することができます。  トレース フラグを指定してクエリを実行するには、サポート技術情報の資料「 [特定のクエリ レベルに対応するさまざまなトレース フラグを使用して制御できる、プランが影響を及ぼす SQL Server クエリ オプティマイザーの動作の有効化](http://support.microsoft.com/kb/2801413)」を参照してください。  
  
## <a name="new-xevents"></a>新しい XEvent  
 新しいクエリ プランをサポートする、2 つの新しい query_optimizer_estimate_cardinality XEvent が存在します。  
  
-   
  *query_optimizer_estimate_cardinality* は、クエリ オプティマイザーが関係式のカーディナリティを推定するときに発生します。  
  
-   
  *query_optimizer_force_both_cardinality_estimation*の動作が発生するのは、トレース フラグ 2312 と 9481 の両方が有効になっていて、古いカーディナリティ推定動作と新しいカーディナリティ推定動作の両方を同時に適用しようとする場合です。  
  
## <a name="examples"></a>使用例  
 次の例では、新しいカーディナリティ推定で加えられた変更の一部を示します。 カーディナリティを推定するコードを書き直しました。 ロジックは複雑であり、すべての変更を網羅した完全な一覧をここに示すことはできません。  
  
> [!NOTE]  
>  これらの例は、概念を示す情報として掲載したものです。 管理者や開発者が、データベースとクエリを設計する方法などに変更を加える必要はありません。  
  
### <a name="example-a-new-cardinality-estimates-use-an-average-cardinality-for-recently-added-ascending-data"></a>例 A。新しいカーディナリティ推定機能は、最近追加された昇順データに関して、平均のカーディナリティを使用します。  
 この例では、最新の統計を更新する際に、テーブル内の最大値を上回る昇順データに関するカーディナリティ推定を、新しいカーディナリティ推定機能がどのように向上させるかを示します。  
  
```  
SELECT item, category, amount FROM dbo.Sales AS s WHERE Date = '2013-12-19';  
```  
  
 この例では、Sales テーブルに新しい行を毎日追加し、クエリは 12/19/2013 (2013 年 12 月 19 日) に発生した行と、12/18/2013 に最後に更新された統計を要求します。 12/19/2013 という日付がテーブル内の最大値を上回っていて、この値を含む形で統計の更新が実行されていないため、以前のカーディナリティ推定機能はこの値が存在しないことを想定していました。 昇順キーの問題と呼ばれるこの状況は、その日のうちにデータを読み込んだ後、統計が更新される前にクエリがデータを要求する場合に発生します。  
  
 この動作は変更されました。 現在は、最後に統計を更新し、その後に追加された最新の昇順データを含む形で統計が更新されていない場合でも、新しいカーディナリティ推定機能はそれらの値が存在することを想定し、カーディナリティ推定を行う際に列内にある各値として平均カーディナリティを使用します。  
  
### <a name="example-b-new-cardinality-estimates-assume-filtered-predicates-on-the-same-table-have-some-correlation"></a>例 B。新しいカーディナリティ推定機能は、同じテーブル内にあるフィルター処理された複数の述語の間に、何かの相関関係があることを想定します。  
 この例では、Cars テーブルに 1,000 の行が存在することを想定します。200 の行では Make (メーカー) は "Honda" になっており、50 の行では Model (車種) は "Civic" になっており、"Civic" の行すべてで Make は "Honda" になっています。 したがって、Make の列では値の 20% が "Honda" になっており、Model の列では値の 5% が "Civic" になっており、"Honda Civic" の実際の数は 50 です。 以前のカーディナリティ推定機能では、Make と Model の各列にある値が互いに独立していることを想定していました。 前のクエリ オプティマイザーの推定が 10 Honda なって (.05 *.20 \* 1,000 行 = 10 行)。  
  
```  
SELECT year, purchase_price FROM dbo.Cars WHERE Make = 'Honda' AND Model = 'Civic';  
```  
  
 この動作は変更されました。 現在の新しいカーディナリティ推定機能は、Make 列と Model 列の間に *「何かの」* 相関関係が存在することを想定します。 クエリ オプティマイザーは、推定式に指数成分を追加することにより、以前の推定を超えるカーディナリティを推定します。 クエリ オプティマイザーが推定 22.36 行 (.05 * SQRT(.20) \* 1,000 行 = 22.36 行)、述語に一致します。 このシナリオと特定のデータ分布の場合は、クエリが返す 22.36 行という値は、実際の値である 50 行に近づきます。  
  
 新しいカーディナリティ推定機能のロジックは、述語選択度を並べ替え、指数を大きくすることに注意してください。 たとえば、述語選択度の.05、.20、および.25 場合、カーディナリティの推定になります (.05 * SQRT(.20) \* SQRT(SQRT(.25)))。  
  
### <a name="example-c-new-cardinality-estimates-assume-filtered-predicates-on-different-tables-are-independent"></a>例 C。新しいカーディナリティ推定機能は、異なるテーブル上でフィルター処理された述語の間で、互いに依存関係がないことを想定しています。  
 この例では、以前のカーディナリティ推定機能は、述語フィルター s.type と r.date が相関していることを想定しています。 ただし、最近のワークロードに対するテストの結果は、異なるテーブル上にある列に対する述語フィルターが互いに相関しないことを示しています。  
  
```  
SELECT s.ticket, s.customer, r.store FROM dbo.Sales AS s CROSS JOIN dbo.Returns AS r  
WHERE s.ticket = r.ticket AND s.type = 'toy' AND r.date = '2013-12-19';  
```  
  
 この動作は変更されました。 現在の新しいカーディナリティ推定機能のロジックは、s.type が r.date に相関しないことを想定しています。 つまり、玩具の返品は特定の 1 日ではなく、毎日発生することを想定しています。 この例では、新しいカーディナリティ推定機能は、以前のカーディナリティ推定機能未満の数を推定します。  
  
## <a name="see-also"></a>参照  
 [パフォーマンスの監視とチューニング](monitor-and-tune-for-performance.md)  
  
  