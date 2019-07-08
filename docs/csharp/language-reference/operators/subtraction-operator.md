---
title: '- 及 -= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 80603107beb708e76a2c7446f300d71ede411570
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609848"
---
# <a name="--and---operators-c-reference"></a>- 及 -= 運算子 (C# 參考)

`-` 運算子受到內建數值型別和 [delegate](../keywords/delegate.md) 型別所支援。

如需算術 `-` 運算子的資訊，請參閱[算術運算子](arithmetic-operators.md)一文中的[一元加號和減號運算子](arithmetic-operators.md#unary-plus-and-minus-operators)與[減法運算子 -](arithmetic-operators.md#subtraction-operator--) 章節。

## <a name="delegate-removal"></a>委派移除

針對相同 [delegate](../keywords/delegate.md) 型別中的運算元，`-` 運算子會傳回委派執行個體，其計算方式如下：

- 如果兩個運算元都為非 Null，且右邊運算元的引動過程清單是左邊運算元之引動過程清單的適當連續子清單，則作業結果會是新引動過程清單藉由從左邊運算元之引動過程清單來移除右邊運算元的項目所取得。 如果右邊運算元清單與左邊運算元清單中的多個連續子清單相符，則只會移除最右邊的相符子清單。 如果移除導致空白清單，則結果是 `null`。

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- 如果右邊運算元的引動過程清單不是左邊運算元之引動過程清單的適當連續子清單，則作業的結果會是左邊運算元。 例如，移除不屬於多點傳送委派的委派就不會執行任何動作，而且會導致多點傳送委派不變。

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  上述範例也會示範在委派移除期間，系統會比較委派執行個體。 例如，從評估相同 [lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)所產生的委派不相等。 如需有關委派等號比較的詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[委派等號比較運算子](~/_csharplang/spec/expressions.md#delegate-equality-operators)一節。

- 如果左邊運算元是 `null`，則作業的結果是 `null`。 如果右邊運算元是 `null`，則作業的結果是左邊運算元。

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

若要結合委派，請使用 [`+` 運算子](addition-operator.md#delegate-combination)。

如需委派型別的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。

## <a name="subtraction-assignment-operator--"></a>減法指派運算子 -=

使用 `-=` 運算子的運算式，例如

```csharp
x -= y
```

相當於

```csharp
x = x - y
```

但只會評估 `x` 一次。
  
下列範例示範 `-=` 運算子的用法：

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

當您取消訂閱[事件](../keywords/event.md)時，您也會使用 `-=` 來指定要移除的事件處理常式方法。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](operator-overloading.md) `-` 運算子。 多載二元 `-` 運算子時，`-=` 運算子也會隱含地多載。 使用者定義型別無法明確地多載 `-=` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[一元減號運算子](~/_csharplang/spec/expressions.md#unary-minus-operator)與[減法運算子](~/_csharplang/spec/expressions.md#subtraction-operator)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [委派](../../programming-guide/delegates/index.md)
- [事件](../../programming-guide/events/index.md)
- [算術運算子](arithmetic-operators.md)
- [ + 及 += 運算子](addition-operator.md)
