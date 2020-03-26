---
title: 開關運算式 - C# 引用
description: 瞭解如何使用 C# 開關運算式進行模式匹配和其他資料內省
ms.date: 03/19/2020
ms.openlocfilehash: 9e609bcea0f92f492b5f9b07840e47f75c1b71e4
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249785"
---
# <a name="switch-expression-c-reference"></a>開關運算式（C# 引用）

本文介紹 C# 8.0 仲介紹的`switch`運算式。 有關該`switch`語句的資訊，請參閱語句部分中[`switch`有關該語句](../keywords/switch.md)的文章。 [statements](../keywords/index.md)

## <a name="basic-example"></a>基本範例

該`switch`運算式在運算式`switch`上下文中提供類似語義。 當開關臂產生值時，它提供了簡潔的語法。 下面的示例顯示了開關運算式的結構。 它將線上地圖中`enum`表示視覺方向的值轉換為相應的基本方向：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

前面的示例顯示了交換器運算式的基本元素：

- *範圍運算式*： 前面的示例使用變數`direction`作為範圍運算式。
- *開關運算式臂*：每個開關運算式臂包含*一個模式*、一個可選*的大小寫保護、*`=>`權杖*和運算式*。

*開關運算式*的結果是第一個*開關運算式臂*的運算式的值，其*模式*與*範圍運算式*匹配，其*原因保護*（如果存在）計算為`true`。 權杖右側的運算式不能是運算式語句。 *expression* `=>`

按文本順序計算*開關運算式臂*。 當無法選擇較低的*開關運算式臂*時，編譯器會發出錯誤，因為較高的*開關運算式臂*與其所有值匹配。

## <a name="patterns-and-case-guards"></a>圖案和外殼防護裝置

交換器運算式臂中支援許多模式。 前面的示例使用了*值模式*。 *值模式*將範圍運算式與值進行比較。 該值必須是編譯時間常量。 *類型模式*將範圍運算式與已知類型進行比較。 以下示例從序列中檢索第三個元素。 它根據序列的類型使用不同的方法：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

模式可以是遞迴的，其中模式測試類型，如果該類型匹配，則模式與範圍運算式上的一個或多個屬性值匹配。 可以使用遞迴模式擴展前面的示例。 為元素少於 3 的陣列添加開關運算式臂。 遞迴模式顯示在以下示例中：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

遞迴模式可以檢查範圍運算式的屬性，但不能執行任意代碼。 可以使用`when`子句中指定的*大小寫保護*為其他序列類型提供類似的檢查：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

最後，您可以添加`_`模式和`null`模式來捕獲任何其他交換器運算式臂未處理的參數。 這使得 switch 運算式*詳盡無遺*，這意味著可以處理範圍運算式的任何可能值。 下面的示例添加這些運算式臂：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

前面的示例添加一個`null`模式，並將`IEnumerable<T>`類型模式更改為`_`模式。 該`null`模式提供作為開關運算式臂的空檢查。 該臂的運算式引發一個<xref:System.ArgumentNullException>。 該`_`模式與以前臂未匹配的所有輸入匹配。 它必須在`null`檢查後出現，否則與輸入匹配`null`。

你可以閱讀更多在C#語言規格建議遞[歸模式](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [模式比對](../../pattern-matching.md)
