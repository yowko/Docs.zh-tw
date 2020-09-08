---
title: 延後執行和延遲評估-LINQ to XML
description: 瞭解延後執行的優點和需求，以及如何使用查詢和軸作業來實現。
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 21b1c7b7d54e7f787919f1e1601fc36bc8c1caff
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552106"
---
# <a name="deferred-execution-and-lazy-evaluation-linq-to-xml"></a>延後執行和延遲評估 (LINQ to XML) 

若要使用延後執行，通常會實作查詢和座標軸運算。 本文說明延後執行的需求和優點，以及一些執行考慮。

## <a name="deferred-execution"></a>延後執行

延後執行是指延遲評估運算式，直到實際需要其「實現的」** 值為止。 當您必須管理大型資料集合，尤其是在包含一系列鏈結之查詢或管理的程式中時，延後執行會明顯改善效能。 在最好的情況下，延後執行僅能單一逐一查看來源集合。

LINQ 技術可讓延後執行大量用於 <xref:System.Linq?displayProperty=nameWithType> 核心類別的成員以及各種 LINQ 命名空間中的擴充方法，例如，<xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>。

在 iterator 區塊中使用時，使用語句) 形式的 [yield (c # 參考) ](../../csharp/language-reference/keywords/yield.md) 關鍵字 (，直接在 c # 語言中支援延後執行 `yield-return` 。 此類 Iterator 必須傳回型別 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> (或衍生型別) 的集合。

## <a name="eager-vs-lazy-evaluation"></a>積極與延遲評估

當您撰寫實作延後執行的方法時，您也必須決定要使用延遲評估或急切評估來實作方法。

- 若為「延遲評估」**，來源集合的單一項目會在每次呼叫 Iterator 時進行處理。 這是實作 Iterator 的一般方式。
- 若為「急切評估」**，第一次呼叫 Iterator 時，就會處理整個集合。 同時，可能也需要來源集合的暫存副本。 例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必須在傳回第一個項目前，排序整個集合。

延遲評估通常會產生較好的效能，因為它會平均分散整個集合評估的負荷處理，並將暫存資料的使用率降到最低。 當然，對於某些運算而言，沒有具體化中繼結果之外的其他選擇。

如需在 c # 和 Visual Basic 中進行程式設計延後執行的範例，請參閱 [延後執行範例](deferred-execution-example.md) 。

## <a name="see-also"></a>另請參閱

- [教學課程：在 C 中一起連結查詢#](chain-queries-example.md)
- [概念和術語 (功能性轉換) ](concepts-terminology-functional-transformation.md)
- [彙總作業 (C#)](../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [ (Visual Basic) 的匯總作業 ](../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
- [yield (C# 參考)](../../csharp/language-reference/keywords/yield.md)
