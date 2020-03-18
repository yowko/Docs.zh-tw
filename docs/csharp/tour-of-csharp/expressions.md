---
title: C# 運算式 - C# 語言教學課程
description: 運算式、運算元及運算子是 C# 語言的建置組塊
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159152"
---
# <a name="expressions"></a>運算式

「運算式」** 是由「運算元」** 和「運算子」** 建構而成。 運算式的運算子會指出要將哪些運算套用到運算元。 運算子範例包括 `+`、`-`、`*`、`/` 及 `new`。 運算元範例包括常值、欄位、區域變數及運算式。

當運算式包含多個運算子時，運算子的「優先順序」** 會控制評估個別運算子的順序。 例如，運算式 `x + y * z` 會評估為 `x + (y * z)`，因為 `*` 運算子的優先順序高於 `+` 運算子。

當兩個優先順序相同的運算子之間有運算元時，運算子的「關聯性」** 會控制執行運算的順序：

* 除了賦值和空合併運算子外，所有二進位運算子都是*左關聯的*，這意味著操作從左至右執行。 例如，`x + y + z` 會判斷值為 `(x + y) + z`。
* 指派運算子、空`??`聚接`??=`運算子和條件運算子`?:`是*右關聯的*，這意味著操作是從右至左執行的。 例如，`x = y = z` 會判斷值為 `x = (y = z)`。

您可以使用括弧來控制優先順序和關聯性。 例如，`x + y * z` 會先將 `y` 乘以 `z`，然後再將結果加到 `x`，而 `(x + y) * z` 則會先將 `x` 與 `y` 相加，然後再將結果乘以 `z`。

大部分的運算子都可以[「多載」**](../language-reference/operators/operator-overloading.md)。 運算子多載可允許針對一個運算元屬於 (或兩個運算元都屬於) 使用者定義之類別或結構型別的運算式，指定使用者定義的運算子實作。

C# 提供數個運算子，用於執行[算術](../language-reference/operators/arithmetic-operators.md)、[邏輯](../language-reference/operators/boolean-logical-operators.md)、[位元和移位](../language-reference/operators/bitwise-and-shift-operators.md)作業以及[相等](../language-reference/operators/equality-operators.md)和[順序](../language-reference/operators/comparison-operators.md)比較。

如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](../language-reference/operators/index.md)。

> [!div class="step-by-step"]
> [上一個](types-and-variables.md)
> [下一個](statements.md)
