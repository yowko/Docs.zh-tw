---
title: 'switch 運算式-c # 參考'
description: '瞭解如何使用 c # switch 運算式進行模式比對和其他資料自我檢查'
ms.date: 01/14/2021
ms.openlocfilehash: 55fef8d351b178fd0ec23847e81e6c56eb1367b0
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536082"
---
# <a name="switch-expression-c-reference"></a>switch 運算式 (c # 參考) 

本文涵蓋 `switch` c # 8.0 中引進的運算式。 如需語句的詳細資訊 `switch` ，請參閱[語句](../keywords/index.md)一節中有關[ `switch` 語句](../keywords/switch.md)的文章。

## <a name="basic-example"></a>基本範例

`switch`運算式會 `switch` 在運算式內容中提供類似的語法。 當 switch arm 產生值時，它會提供簡潔的語法。 下列範例顯示 switch 運算式的結構。 它會將 `enum` 線上地圖中表示視覺方向的值轉譯為對應的基線方向：

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

上述範例顯示 switch 運算式的基本元素：

- *範圍運算式*：上述範例會使用變數 `direction` 作為範圍運算式。
- *交換器運算式* arm：每個 switch 運算式 arm 都包含一個 *模式*，也就是選擇性的 *案例防護*、 `=>` token 和 *運算式*。

*Switch 運算式* 的結果是第一個 *switch 運算式 arm* 的運算式 *值，其**模式* 符合 *範圍運算式*，而如果有的話，則會評估為 `true` 。 Token 右邊的 *運算式* `=>` 不可以是運算式語句。

*切換運算式臂* 會以文字順序進行評估。 因為較高的 *switch 運算式 arm* 符合其所有值，所以無法選擇較低的 *switch 運算式 arm* 時，編譯器會發出錯誤。

## <a name="patterns-and-case-guards"></a>模式和案例防護

Switch 運算式臂支援許多模式。 上述範例使用 *常數模式*。 *常數模式* 會將範圍運算式與值進行比較。 該值必須是編譯時間常數。 *型別模式* 會比較範圍運算式與已知型別。 下列範例會從序列中取出第三個元素。 它會根據序列的類型使用不同的方法：

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

模式可以是遞迴，其中的模式會測試型別，而且如果該型別相符，則模式會符合範圍運算式上的一或多個屬性值。 您可以使用遞迴模式來擴充上述範例。 您可以針對擁有少於3個元素的陣列加入 switch 運算式臂。 遞迴模式如下列範例所示：

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

遞迴模式可以檢查範圍運算式的屬性，但是無法執行任意程式碼。 您可以使用子句中指定的 *case guard* `when` ，以提供與其他序列類型類似的檢查：

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

最後，您可以新增 `_` 模式和模式， `null` 以攔截任何其他 switch 運算式 arm 未處理的引數。 這會讓 switch 運算式成為 *詳盡* 的，這表示會處理任何可能的範圍運算式值。 下列範例會新增這些運算式臂：

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

上述範例會新增 `null` 模式，並將型別 `IEnumerable<T>` 模式變更為 `_` 模式。 此 `null` 模式會提供 null 檢查作為 switch 運算式 arm。 該 arm 的運算式會擲回 <xref:System.ArgumentNullException> 。 `_`模式會比對所有未由先前的 arm 相符的輸入。 它必須在檢查之後 `null` ，否則會符合 `null` 輸入。

## <a name="non-exhaustive-switch-expressions"></a>非徹底的 switch 運算式

如果 switch 運算式的模式都沒有攔截引數，則執行時間會擲回例外狀況。 在 .NET Core 3.0 和更新版本中，例外狀況為 <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType> 。 在 .NET Framework 中，例外狀況為 <xref:System.InvalidOperationException> 。

## <a name="see-also"></a>另請參閱

- [遞迴模式的 c # 語言規格提案](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)
- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [模式比對](../../pattern-matching.md)
