---
title: 'switch 運算式-c # 參考'
description: '瞭解如何使用 c # switch 運算式進行模式比對和其他資料自我檢查'
ms.date: 03/19/2020
ms.openlocfilehash: f53cbe873c841271f64496e4e5ff1f11750c7b8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140671"
---
# <a name="switch-expression-c-reference"></a>switch 運算式（c # 參考）

本文涵蓋 c # `switch` 8.0 中引進的運算式。 如需`switch`語句的詳細資訊，請參閱[語句](../keywords/index.md)一節中有關[ `switch`語句](../keywords/switch.md)的文章。

## <a name="basic-example"></a>基本範例

`switch`運算式會在運算式`switch`內容中提供類似的語義。 當交換器臂產生值時，它會提供精簡的語法。 下列範例會顯示 switch 運算式的結構。 它會從線上地圖`enum`中代表視覺方向的值轉譯為對應的基線方向：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

上述範例顯示 switch 運算式的基本元素：

- *範圍運算式*：上述範例會使用變數`direction`做為範圍運算式。
- *交換器運算式*arm：每個交換器運算式 arm 包含*模式*、選擇性的*案例防護*、 `=>`權杖和*運算式*。

*Switch 運算式*的結果是第一個*switch 運算式 arm*的運算式值，其*模式*符合*範圍運算式*，而其*case guard*（如果有的話）會評估為`true`。 Token 右邊的運算式不可以是運算式語句。 *expression* `=>`

*切換運算式臂*會以文字順序進行評估。 當無法選擇較低的*交換器運算式 arm*時，編譯器會發出錯誤，因為較高的*交換器運算式 arm*符合其所有值。

## <a name="patterns-and-case-guards"></a>模式和案例防護

交換器運算式臂支援許多模式。 上述範例使用了*值模式*。 *值模式*會將範圍運算式與值進行比較。 該值必須是編譯時間常數。 *型別模式*會比較範圍運算式與已知型別。 下列範例會從序列中抓取第三個元素。 它會根據順序的類型來使用不同的方法：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

模式可以是遞迴的，其中模式會測試類型，如果該類型符合，則模式會比對範圍運算式上的一或多個屬性值。 您可以使用遞迴模式來擴充先前的範例。 針對具有少於3個元素的陣列，您可以加入切換運算式臂。 遞迴模式如下列範例所示：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

遞迴模式可以檢查範圍運算式的屬性，但無法執行任意程式碼。 您可以使用`when`子句中指定的「*案例防護*」，針對其他序列類型提供類似的檢查：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

最後，您可以新增`_`模式和`null`模式，以攔截未由任何其他交換器運算式 arm 處理的引數。 這會讓 switch 運算式*詳盡*，這表示會處理範圍運算式的任何可能值。 下列範例會新增那些運算式臂：

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

上述範例會加入`null`模式，並將`IEnumerable<T>`類型模式變更為`_`模式。 此`null`模式會提供 null 檢查做為交換器運算式 arm。 該 arm 的運算式會擲回<xref:System.ArgumentNullException>。 此`_`模式會比對先前臂未符合的所有輸入。 它必須位於`null`檢查之後，否則會符合`null`輸入。

您可以在[遞迴模式](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)的 c # 語言規格提案中閱讀更多。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C # 運算子](index.md)
- [模式比對](../../pattern-matching.md)
