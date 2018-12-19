---
title: += 運算子 - C# 參考
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: 5d48f2fe53a9bb6f781f8d35f1e0983bcaa30f88
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240927"
---
# <a name="-operator-c-reference"></a>+= 運算子 (C# 參考)

加法指派運算子。

使用 `+=` 運算子的運算式，例如

```csharp
x += y
```

相當於

```csharp
x = x + y
```

但只會評估 `x` 一次。
  
針對數值型別，[加法運算子](addition-operator.md) `+` 會計算其運算元的和。 如果其中一或兩個運算元的型別為 [string](../keywords/string.md)，則它會串連其運算元的字串表示。 針對委派型別，`+` 運算子會傳回為其運算元組合的新委派執行個體。

當您訂閱[事件](../keywords/event.md)時，您也會使用 `+=` 來指定事件處理常式方法。 如需詳細資訊，請參閱[＜How to：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

下列範例示範 `+=` 運算子的用法：

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a>運算子是否可多載

如果使用者定義的型別將[加法運算子](addition-operator.md) `+` [多載](../keywords/operator.md)，則加法指派運算子 `+=` 會隱含地多載。 使用者定義型別無法明確地多載其他指派運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)及[事件指派](~/_csharplang/spec/expressions.md#event-assignment)章節。
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [事件](../../programming-guide/events/index.md)
- [委派](../../programming-guide/delegates/index.md)
