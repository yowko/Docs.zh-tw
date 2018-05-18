---
title: 將陣列當做物件 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 07e824d21ffc02ba7a3c33507d22d1dc7a1ac638
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="arrays-as-objects-c-programming-guide"></a>將陣列當做物件 (C# 程式設計手冊)
在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。 <xref:System.Array> 是所有陣列類型的抽象基底類型。 您可以使用 <xref:System.Array> 擁有的屬性和其他類別成員。 此種範例會使用 <xref:System.Array.Length%2A> 屬性取得陣列的長度。 下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [陣列](../../../csharp/programming-guide/arrays/index.md)  
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
