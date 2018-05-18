---
title: 一維陣列 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 2f5dcb032c5dea764cdd212bbcd02e1640089d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>一維陣列 (C# 程式設計手冊)
您可以宣告五個整數的一維陣列，如下列範例所示：  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 這個陣列包含從 `array[0]` 到 `array[4]` 的項目。 [new](../../../csharp/language-reference/keywords/new.md) 運算子是用來建立陣列，並將陣列元素初始化為其預設值。 在此範例中，所有陣列元素都會初始化為零。  
  
 儲存字串項目的陣列可以使用相同的方式進行宣告。 例如:   
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>陣列初始化  
 可以在宣告時初始化陣列，在此情況下，不需要陣序規範，因為它已由初始化清單中的項目數所提供。 例如:   
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 字串陣列可以使用相同的方式進行初始化。 以下是字串陣列宣告，其中都會以日名稱初始化每個陣列元素：  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 當您在宣告時初始化陣列時，可以使用下列快速鍵：  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 您可以在不進行初始化的情況下宣告陣列變數，但必須在將陣列指派給變數時使用 `new` 運算子。 例如:   
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0 引進隱含型別陣列。 如需詳細資訊，請參閱[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。  
  
## <a name="value-type-and-reference-type-arrays"></a>實值型別和參考型別陣列  
 請考慮下列陣列宣告：  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 此陳述式的結果取決於 `SomeType` 是實值型別還是參考型別。 如果它是實值型別，陳述式會建立 10 個項目的陣列，且每個都具有 `SomeType` 類型。 如果 `SomeType` 是參考型別，陳述式會建立 10 個項目的陣列，且每個都會初始化為 Null 參考。  
  
 如需實值型別和參考型別的詳細資訊，請參閱[類型](../../../csharp/language-reference/keywords/types.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Array>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [陣列](../../../csharp/programming-guide/arrays/index.md)  
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
