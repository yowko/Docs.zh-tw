---
title: '&amp; 運算子 (C# 參考)'
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: a8f76ded0ef9f8e8099838a903d90f1695324991
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "43510974"
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

[條件式 AND 運算子](conditional-and-operator.md) `&&` 也會計算其運算元的邏輯 AND，但只有在第一個運算元的值為 `true` 時，才會求第二個運算元的值。

若是可為 Null 的 bool 運算元，`&` 運算子的行為與 SQL 的三值邏輯一致。 如需詳細資訊，請參閱[使用可為 Null 的型別](../../programming-guide/nullable-types/using-nullable-types.md)一文的 [bool? 型別](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type)一節。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md)二元 `&` 運算子。 多載二元 `&` 運算子時，[AND 指派運算子](and-assignment-operator.md) `&=` 也會隱含地多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[傳址運算子](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)及[邏輯運算子](~/_csharplang/spec/expressions.md#logical-operators)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [| 運算子](or-operator.md)
- [^ 運算子](xor-operator.md)
- [~ 運算子](bitwise-complement-operator.md)
- [&& 運算子](conditional-and-operator.md)
