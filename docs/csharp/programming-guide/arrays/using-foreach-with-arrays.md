---
title: 搭配陣列使用 foreach (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 8511d9dd3b7155d2f6bca229f264071b54ed173b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>搭配陣列使用 foreach (C# 程式設計手冊)
C# 還提供 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式。 這個陳述式提供了一個簡單且清楚的方法來逐一查看陣列中或任何可列舉集合中的元素。 `foreach` 陳述式會依照陣列或集合類型的列舉值傳回的順序處理元素，通常是從第 0 個元素到最後一個元素。 例如，下列程式碼會建立名為 `numbers` 的陣列，並使用 `foreach` 陳述式逐一查看該陣列：  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 使用多維陣列時，就可以使用相同的方法來逐一查看元素，例如：  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 但是在使用多維陣列時，使用巢狀 [for](../../../csharp/language-reference/keywords/for.md) 迴圈能夠讓您進一步控制陣列元素。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Array>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [陣列](../../../csharp/programming-guide/arrays/index.md)  
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
