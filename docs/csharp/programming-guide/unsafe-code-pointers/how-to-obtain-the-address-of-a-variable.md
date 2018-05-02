---
title: 如何：取得變數位址 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63a49490effb8b7d365492e8518b7558ec03a705
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>如何：取得變數位址 (C# 程式設計手冊)
若要取得評估為固定變數之一元運算式的位址，請使用傳址運算子 `&`：  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 傳址運算子只能套用至變數。 如果變數是可移動的變數，您可以使用 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)暫時修正變數，然後再取得其位址。  
  
 您必須負責確保變數已初始化。 如果變數未初始化，編譯器不會發出錯誤訊息。  
  
 您無法取得常數或值的位址。  
  
## <a name="example"></a>範例  
 在此範例中，`int`、`p` 的指標會宣告並指派 `number` 整數變數的位址。 `number` 變數會初始化，作為指派給 `*p` 的結果。 如果您將這個指派陳述式標記為註解，即會移除 `number` 變數的初始化，而不會發出任何編譯時錯誤。  

> [!NOTE]
> 請使用 [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項來編譯此範例。
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [型別](../../../csharp/language-reference/keywords/types.md)  
 [Unsafe.DangerousAPI](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
