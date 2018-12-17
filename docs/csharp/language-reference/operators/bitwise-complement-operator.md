---
title: ~ 運算子 - C# 參考
ms.custom: seodec18
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 57e5baee423c0b5d9292d0ad4cbf909646eb3a38
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235714"
---
# <a name="-operator-c-reference"></a>~ 運算子 (C# 參考)

位元補數運算子 `~` 是一元運算子，會藉由反轉每個位元來產生其運算元的位元補數。 所有整數型別都支援 `~` 運算子。

> [!NOTE]
> `~` 符號也可用來宣告完成項。 如需詳細資訊，請參閱[完成項](../../programming-guide/classes-and-structs/destructors.md)。

下列範例示範 `~` 運算子的用法：

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> 上述範例使用[在 C# 7.0 中導入](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements)並[在 C# 7.2 中增強的](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals)二進位常值。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `~` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[位元補數運算子](~/_csharplang/spec/expressions.md#bitwise-complement-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [完成項](../../programming-guide/classes-and-structs/destructors.md)
- [& 運算子](and-operator.md)
- [| 運算子](or-operator.md)
- [^ 運算子](xor-operator.md)
