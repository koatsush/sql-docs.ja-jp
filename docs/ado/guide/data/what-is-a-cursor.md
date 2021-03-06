---
title: カーソルとは | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], about cursors
ms.assetid: 596eb4b6-c22f-4cde-b23f-172dd66c3161
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d903b2a5f971d0b6c7114a9e5229bff6133d743
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923455"
---
# <a name="what-is-a-cursor"></a>カーソルとは
リレーショナル データベースで操作を実行する場合、行の完全なセットが操作の対象になります。 SELECT ステートメントでは、WHERE 句で指定した条件を満たすすべての行のセットが返されます。 このステートメントが返す行の完全なセットを結果セットと呼びます。 全体の結果セットを単位としてでは、アプリケーション、特に対話型と、オンラインであるが効率的に作業常にことはできません。 そのため、このようなアプリケーションでは、一度に 1 行または少数の行のブロックを使用するためのメカニズムが必要になります。 カーソルはそのメカニズムを提供する結果セットの拡張機能です。  
  
 カーソルは、カーソル ライブラリによって実装されます。 カーソル ライブラリは、ソフトウェア、データベース システムまたはデータ アクセス API の一部として実装される多くの場合、データ ソース (結果セット) から返されるデータの属性を管理するために使用します。 これらの属性が、同時実行の管理、行の数が返される結果セットに配置し、前方または後方を移動するかどうか (または両方) 結果を設定 (スクロール) します。  
  
 カーソルの結果セット内の位置を追跡し、または元のテーブルを返さずに、結果セットに対して 1 行ずつの複数の操作を実行することができます。 つまり、カーソルでは、概念的には、データベース内のテーブルに基づく結果セットを返します。 カーソル名前は、結果セット内の現在位置を示すため、コンピューター画面上にカーソルが現在の位置を示すと同様です。  
  
 ADO では、その使用方法の詳細を説明する前にカーソルの概念について理解を深めるには重要です。  
  
 カーソルを使用して、以下の操作を実行できます。  
  
-   結果セット内の特定の行の位置を指定します。  
  
-   1 つの行または現在の結果セットの位置に基づく行のブロックを取得します。  
  
-   結果セット内の現在位置にある行のデータを変更します。  
  
-   その他のユーザーによって行われたデータの変更をさまざまなレベルの応答性を定義します。  
  
 たとえば、潜在的な購入者に利用可能な製品の一覧を表示するアプリケーションを検討してください。 購入者は、製品の詳細と、コストを表示する一覧をスクロールし、最後に購入する製品を選択します。 追加のスクロールと選択リストの残りの部分に発生します。 に関しては購入者として、一度に 1 つずつ、製品が表示されますが、アプリケーションでは、スクロール可能なカーソルを使用して、結果セットを上下に参照します。  
  
 さまざまな方法でカーソルを使用することができます。  
  
-   すべての行の存在しません。  
  
-   一部またはすべての 1 つのテーブルの行。  
  
-   一部またはすべての論理的に結合されたテーブルから行。  
  
-   読み取り専用またはとカーソルまたはフィールド レベルで更新できます。  
  
-   順方向専用、または完全にスクロール可能です。  
  
-   で、カーソルのキーセット サーバーに配置します。  
  
-   (メンバーシップ、並べ替え、挿入、更新、削除など) には、その他のアプリケーションで発生した基になるテーブルの変更に影響します。  
  
-   サーバーまたはクライアント上に存在します。  
  
 読み取り専用カーソルは、ユーザーが、結果セットを参照し、読み取り/書き込みカーソルが個別の行の更新プログラムを実装に役立ちます。 ベース テーブルの行を指すキーセットでは、複雑なカーソルを定義できます。 一部のカーソルは読み取り専用、順方向には、他のユーザー双方向に移動し、その他のアプリケーションが実行するデータベースの変更に基づく結果セットを動的に更新を提供できます。  
  
 すべてのアプリケーションは、データ アクセスまたは更新にカーソルを使用する必要があります。 単に、いくつかのクエリはカーソルを使用して行を直接の更新を必要はありません。 カーソルが最後にデータを取得する手法のいずれかを指定する必要があります-、カーソルを使用する場合は、影響が最も低いカーソルを選択する必要があります。 結果セットがカーソルを使用して更新可能ではありませんが、ストアド プロシージャを使用して結果セットを作成するときに編集またはメソッドを更新します。  
  
## <a name="concurrency"></a>コンカレンシー  
 一部のマルチ ユーザー アプリケーションでは、できる限り最新にするには、エンドユーザーに表示されるデータのことが重要です。 古典的な例のようなシステムは、航空券予約システムでは、特定のフライト (およびそのため、1 つのレコード) で同じ座席の多くのユーザーを競合する可能性があります。 このような場合は、アプリケーションの設計は、1 つのレコードでの同時操作を処理する必要があります。  
  
 他のアプリケーションでは、同時実行は重要ではないです。 このような場合は、常に現在のデータを管理することで費用を正当化されることはできません。  
  
## <a name="position"></a>位置  
 カーソルもの追跡結果セット内の現在の位置。 考える、カーソルの位置と同じように、現在のレコードへのポインターとして配列インデックスが指す配列内の特定の場所にある値。  
  
## <a name="scrollability"></a>スクロール可能  
 アプリケーションで採用されているカーソルの種類にも影響が結果セット内の行を前方と後方に移動する機能これは、スクロール機能と呼ばれます。 前方に移動する機能*と*の結果から旧バージョンとセットは、カーソルの複雑さを追加しを実装する方が高くなります。 このため、必要な場合にのみ、この機能により、カーソルを要求する必要があります。
