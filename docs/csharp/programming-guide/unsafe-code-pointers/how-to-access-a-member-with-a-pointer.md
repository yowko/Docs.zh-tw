---
title: 使用指標存取成員 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 153e5f1cfc1f4f8309a31ab58d699a273b417563
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546487"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>如何：使用指標存取成員 (C# 程式設計手冊)
若要存取在不安全內容中宣告的結構成員，您可以使用下例所示的成員存取運算子，該例的 `p` 是包含成員 `x` 的 [struct](../../../csharp/language-reference/keywords/struct.md) 的指標。  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>範例  
 在本例中，會宣告並具現化包含 `x` 和 `y` 兩個座標的 [struct](../../../csharp/language-reference/keywords/struct.md) (`CoOrds`)。 藉由使用成員存取運算子 `->` 和執行個體 `home` 的指標，`x` 和 `y` 成為指派的值。  
  
> [!NOTE]
>  請注意，運算式 `p->x` 相當於運算式 `(*p).x`，而且您可以使用任一運算式取得相同的結果。  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型別](../../../csharp/language-reference/keywords/types.md)
- [Unsafe.DangerousAPI](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
