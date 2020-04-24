---
title: + 及 += 運算子 - C# 參考
ms.date: 04/23/2020
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 18364d80b8117fd4074c2c4231eac07c76829bb3
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135733"
---
# <a name="-and--operators-c-reference"></a>+ 及 += 運算子 (C# 參考)

內`+`建`+=` [整數](../builtin-types/integral-numeric-types.md)和[浮點數](../builtin-types/floating-point-numeric-types.md)類型、[字串](../builtin-types/reference-types.md#the-string-type)類型和[委派](../builtin-types/reference-types.md#the-delegate-type)類型都支援和運算子。

如需算術 `+` 運算子的資訊，請參閱[算術運算子](arithmetic-operators.md)一文中的[一元加號和減號運算子](arithmetic-operators.md#unary-plus-and-minus-operators)與[加法運算子 +](arithmetic-operators.md#addition-operator-) 章節。

## <a name="string-concatenation"></a>字串串連

當其中一個或兩個運算元的[string](../builtin-types/reference-types.md#the-string-type)類型為 string `+`時，運算子會串連其運算元的字串表示（的字串`null`表示為空字串）：

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

從 c # 6 開始，[字串插補](../tokens/interpolated.md)可讓您更方便地格式化字串：

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>委派組合

針對相同[委派](../builtin-types/reference-types.md#the-delegate-type)型別中的運算元，`+` 運算子會傳回新的委派執行個體，並在叫用時叫用左側運算元，然後叫用右側運算元。 如果其中任一個運算元為 `null`，則 `+` 運算子會傳回另一個運算元的值 (也有可能是 `null`)。 下列範例顯示委派如何與 `+` 運算子結合：

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

若要執行委派移除，請使用[ `-`運算子](subtraction-operator.md#delegate-removal)。

如需委派型別的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。

## <a name="addition-assignment-operator-"></a>加法指派運算子 +=

使用 `+=` 運算子的運算式，例如

```csharp
x += y
```

相當於

```csharp
x = x + y
```

但只會評估 `x` 一次。

下列範例示範 `+=` 運算子的用法：

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

當您訂閱[事件](../keywords/event.md)時，您也會使用 `+=` 來指定事件處理常式方法。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](operator-overloading.md)`+` 運算子。 多載二元 `+` 運算子時，`+=` 運算子也會隱含地多載。 使用者定義型別無法明確地多載 `+=` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[一元加號運算子](~/_csharplang/spec/expressions.md#unary-plus-operator)與[加法運算子](~/_csharplang/spec/expressions.md#addition-operator)小節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C # 運算子](index.md)
- [如何串連多個字串](../../how-to/concatenate-multiple-strings.md)
- [事件](../../programming-guide/events/index.md)
- [算術運算子](arithmetic-operators.md)
- [- 及 = 運算子](subtraction-operator.md)
