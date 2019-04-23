---
title: '&amp; 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310040"
---
# <a name="amp-operator-c-reference"></a>&amp; 運算子 (C# 參考)

`&` 運算子支援兩種形式：一元傳址運算子或二元邏輯運算子。

## <a name="unary-address-of-operator"></a>一元傳址運算子

一元 `&` 運算子會傳回其運算元的位址。 如需詳細資訊，請參閱[如何：取得變數位址](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md)。

傳址運算子 `&` 需要 [unsafe](../keywords/unsafe.md) 內容。

## <a name="integer-logical-bitwise-and-operator"></a>整數邏輯位元 AND 運算子

若為整數型別，`&` 運算子會計算其運算元的邏輯位元 AND：

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> 上述範例會使用在 [C# 7.0 中推出](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements)並[在 C# 7.2 增強的](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals)二進位常值。

因為對整數型別進行的運算通常也可對列舉行別進行，所以 `&` 運算子也支援 [enum](../keywords/enum.md) 運算元。

## <a name="boolean-logical-and-operator"></a>布林值邏輯 AND 運算子

若為 [bool](../keywords/bool.md) 運算元，`&` 運算子會計算其運算元的邏輯 AND。 若 `x` 及 `y` 皆為 `true`，那麼 `x & y` 的結果會是 `true`。 否則，結果為 `false`。

即使第一個運算元的值為 `false`，`&` 運算子仍會求這兩個運算元的值，所以不論第二個運算元的值為何，其結果必定為 `false`。 下列範例示範了該行為：

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

[條件式 AND 運算子](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` 也會計算其運算元的邏輯 AND，但在第一個運算元的值評估為 `false` 時，則不會評估第二個運算元。

若是可為 Null 的 bool 運算元，`&` 運算子的行為與 SQL 的三值邏輯一致。 如需詳細資訊，請參閱[布林值邏輯運算子](boolean-logical-operators.md)一文的[可為 Null 的布林值邏輯運算子](boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md)二元 `&` 運算子。 多載二元 `&` 運算子時，[AND 指派運算子](and-assignment-operator.md) `&=` 也會隱含地多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[傳址運算子](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)及[邏輯運算子](~/_csharplang/spec/expressions.md#logical-operators)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計手冊](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [布林值邏輯運算子](boolean-logical-operators.md)
- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [| 運算子](or-operator.md)
- [^ 運算子](xor-operator.md)
- [~ 運算子](bitwise-complement-operator.md)
