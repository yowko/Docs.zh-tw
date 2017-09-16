---
title: "如何：使用指標存取成員 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ca24b7d930e7b6c61a3db89a431f1ec3aaec77c8
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

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
  
 [!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

