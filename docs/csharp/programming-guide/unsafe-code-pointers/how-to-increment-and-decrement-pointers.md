---
title: 操作說明：遞增和遞減指標 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: ead179c3711a5e63bbdc2ec2b5644d5991b82ee7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573266"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>操作說明：遞增和遞減指標 (C# 程式設計手冊)

針對型別 `pointer-type*` 的指標，使用遞增和遞減運算子 (`++` 和 `--`)，依 `sizeof(pointer-type)` 變更指標位置。 遞增和遞減運算式的格式如下：  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 遞增和遞減運算子可以套用至任何類型的指標，類型 `void*` 除外。  
  
 將遞增運算子套用至型別 `pointer-type*` 之指標的效果，是將 `sizeof(pointer-type)` 加入至指標變數內含的位址。  
  
 將遞減運算子套用至型別 `pointer-type*` 之指標的效果，是從指標變數內含的位址中減去 `sizeof(pointer-type)`。  
  
 如果運算讓指標的定義域溢位，而且結果取決於實作，則不會產生任何例外狀況。  
  
## <a name="example"></a>範例  
 在此範例中，您要按 `int` 大小遞增指標逐步執行陣列。 您會在每個步驟顯示陣列元素的位址和內容。  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
**值：0 @ 位址：12860272**
**值：1 @ 位址：12860276**
**值：2 @ 位址：12860280**
**值：3 @ 位址：12860284**
**值：4 @ 位址：12860288**

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
- [指標操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型別](../../../csharp/language-reference/keywords/types.md)
- [Unsafe.DangerousAPI](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
- [sizeof](../../../csharp/language-reference/keywords/sizeof.md)
