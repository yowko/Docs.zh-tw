---
title: 如何：使用指標存取陣列元素 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 92eb7a79c0e7522d1474537aeefbfdb083a11dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>如何：使用指標存取陣列元素 (C# 程式設計手冊)
在不安全的內容中，您可以使用指標元素存取來存取記憶體中的元素，如下例所示：  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 方括弧中的運算式必須以隱含方式轉換成 `int`、`uint`、`long` 或 `ulong`。 作業 p[e] 相當於 *(p+e)。 如同 C 和 C++，指標元素存取不會檢查超出範圍的錯誤。  
  
## <a name="example"></a>範例  
 在此範例中，123 記憶體位置是配置在字元陣列 `charPointer`。 陣列是用來顯示兩個 [for](../../../csharp/language-reference/keywords/for.md) 迴圈中的小寫字母和大寫字母。  
  
 請注意，運算式 `charPointer[i]` 相當於運算式 `*(charPointer + i)`，而且您可以使用任一運算式取得相同的結果。  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 **大寫字母：**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**小寫字母：**  
**abcdefghijklmnopqrstuvwxyz**   
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [型別](../../../csharp/language-reference/keywords/types.md)  
 [Unsafe.DangerousAPI](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
