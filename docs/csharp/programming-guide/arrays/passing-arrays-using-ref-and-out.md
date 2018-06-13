---
title: 使用 ref 和 out 傳遞陣列 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: a186399125e01bb2535f3a8b488c6fbd85932246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313566"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>使用 ref 和 out 傳遞陣列 (C# 程式設計手冊)
如同所有的 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數，陣列類型的 `out` 參數必須先指派才能使用，也就是說，被呼叫端必須先指派這個參數。 例如:   
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 如同所有的 [ref](../../../csharp/language-reference/keywords/ref.md) 參數，陣列類型的 `ref` 參數也必須由呼叫端明確指派。 因此，被呼叫端就不需要明確指派該參數。 呼叫的結果可能會修改陣列類型的 `ref` 參數。 例如，陣列可以擁有指派的 [null](../../../csharp/language-reference/keywords/null.md) 值，或是初始化為不同的陣列。 例如:   
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 下列兩個範例將示範在陣列傳遞至方法時使用 `out` 和 `ref` 之間的差異。  
  
## <a name="example"></a>範例  
 在這個範例中，`theArray` 陣列是在呼叫端 (`Main` 方法) 宣告，並且在 `FillArray` 方法中進行初始化。 接著陣列元素會傳回呼叫端並顯示。  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>範例  
 在這個範例中，`theArray` 陣列是在呼叫端 (`Main` 方法) 進行初始化，並且會使用 `FillArray` 參數將該陣列傳遞至 `ref` 方法。 有些陣列元素會在 `FillArray` 方法中更新。 接著陣列元素會傳回呼叫端並顯示。  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>請參閱  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [out 參數修飾詞](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [陣列](../../../csharp/programming-guide/arrays/index.md)  
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
