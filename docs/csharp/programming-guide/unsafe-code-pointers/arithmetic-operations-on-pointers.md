---
title: 指標的算術運算 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: 94e5d3fbf250f8b99560f83e14c063142ac7ad29
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242096"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>指標的算術運算 (C# 程式設計手冊)
本主題討論如何使用 `+` 和 `-` 算術運算子來操作指標。  
  
> [!NOTE]
>  您無法對 void 指標執行任何算術運算。  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>加入和減去指標的數值  
 您可以將型別 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) 的 `n` 值加入到指標。 如果 `p` 是型別 `pointer-type*` 的指標，則結果 `p+n` 是將 `n * sizeof(pointer-type)` 加入到 `p` 位址所產生的指標。 同樣地，`p-n` 是將 `p` 位址減去 `n * sizeof(pointer-type)` 所產生的指標。  
  
## <a name="subtracting-pointers"></a>減去指標  
 您也可以減去相同類型的指標。 結果的類型一律是 `long`。 例如，如果 `p1` 和 `p2` 是 `pointer-type*` 類型的指標，則 `p1-p2` 運算式會導致：  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 如果算術運算讓指標的定義域溢位，而且結果取決於實作，則不會產生任何例外狀況。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)  
- [指標操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [型別](../../../csharp/language-reference/keywords/types.md)  
- [Unsafe.DangerousAPI](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
