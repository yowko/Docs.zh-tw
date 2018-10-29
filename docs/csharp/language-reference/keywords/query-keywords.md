---
title: 查詢關鍵字 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 9ec163e1de018bd87348a5b39a1f34654d7d6d84
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028728"
---
# <a name="query-keywords-c-reference"></a>查詢關鍵字 (C# 參考)

本節包含查詢運算式中所使用的內容關鍵字。

## <a name="in-this-section"></a>本節內容

|子句|描述|
|------------|-----------------|
|[from](from-clause.md)|指定資料來源和範圍變數 (與反覆運算變數類似)。|
|[where](where-clause.md)|根據以邏輯 AND 和 OR 運算子區隔的一或多個布林運算式，以篩選來源項目 (`&&` 或 <code>&#124;&#124;</code>)。|
|[select](select-clause.md)|指定在執行查詢時，所傳回序列中的項目會有的類型和形狀。|
|[group](group-clause.md)|根據指定的索引鍵值來群組查詢結果。|
|[into](into.md)|提供可作為 join、group 或 select 子句結果參考的識別碼。|
|[orderby](orderby-clause.md)|根據項目類型的預設比較子，以遞增或遞減順序來排序查詢結果。|
|[join](join-clause.md)|根據兩個指定比對準則的相等比較，以聯結兩個資料來源。|
|[let](let-clause.md)|引進範圍變數以儲存查詢運算式中的子運算式結果。|
|[in](in.md)|[join](join-clause.md) 子句中的內容關鍵字。|
|[on](on.md)|[join](join-clause.md) 子句中的內容關鍵字。|
|[equals](equals.md)|[join](join-clause.md) 子句中的內容關鍵字。|
|[by](by.md)|[group](group-clause.md) 子句中的內容關鍵字。|
|[ascending](ascending.md)|[orderby](orderby-clause.md) 子句中的內容關鍵字。|
|[descending](descending.md)|[orderby](orderby-clause.md) 子句中的內容關鍵字。|

## <a name="see-also"></a>另請參閱

- [C# 關鍵字](index.md)
- [LINQ (Language-Integrated Query)](../../programming-guide/concepts/linq/index.md)
- [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [開始使用 C# 中的 LINQ](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)