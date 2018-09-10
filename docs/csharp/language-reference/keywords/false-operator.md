---
title: false 運算子 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272133"
---
# <a name="false-operator-c-reference"></a>false 運算子 (C# 參考)

若運算元為 `false` 即傳回 [bool](bool.md) 值 `true`；否則傳回 `false`。

在 C# 2.0 之前，`true` 和 `false` 運算子是用來建立使用者定義之可為 Null 的實值型別，該類型與 `SqlBool` 等類型相容。 不過，該語言現在針對可為 Null 的實值型別提供內建支援，因此您應盡可能使用這些類型，而不是多載 `true` 和 `false` 運算子。 如需詳細資訊，請參閱[可為 Null 的型別](../../programming-guide/nullable-types/index.md)。

使用可為 Null 的布林值時，運算式 `a != b` 不一定等於 `!(a == b)`，因為其中一個或兩個值可能為 Null。 您必須分別多載 `true` 和 `false` 運算子，以正確處理運算式中的 Null 值。 下列範例示範如何多載和使用 `true` 和 `false` 運算子。

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

多載 `true` 和 `false` 運算子的類型可用於 [if](if-else.md)、[do](do.md)、[while](while.md) 和 [for](for.md) 陳述式以及[條件運算式](../operators/conditional-operator.md)中的控制運算式。

如果類型定義了運算子 `false`，則必須同時定義運算子 [true](true.md)。

類型不能直接多載條件邏輯運算子 [&&](../operators/conditional-and-operator.md) 和 [&#124;&#124;](../operators/conditional-or-operator.md)，但藉由多載一般邏輯運算子以及 `true` 和 `false` 運算子，也可達到同樣效果。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)  
- [C# 程式設計指南](../../programming-guide/index.md)  
- [C# 關鍵字](index.md)  
- [C# 運算子](../operators/index.md)  
- [true](true.md)  