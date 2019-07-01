---
title: 一維陣列 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: d221cb9071a2c58f9d7068d5a43dd3a750ba716b
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398564"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>一維陣列 (C# 程式設計手冊)

您可以宣告五個整數的一維陣列，如下列範例所示：  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 這個陣列包含從 `array[0]` 到 `array[4]` 的項目。 [new](../../../csharp/language-reference/operators/new-operator.md) 運算子是用來建立陣列，並將陣列元素初始化為其預設值。 在此範例中，所有陣列元素都會初始化為零。  
  
 儲存字串項目的陣列可以使用相同的方式進行宣告。 例如：  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>陣列初始化

 您可以在宣告時將陣列初始化，在此情況下，因為長度規範已由初始化清單中的項目數所提供，所以不需要長度規範。 例如：  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 字串陣列可以使用相同的方式進行初始化。 以下是字串陣列宣告，其中都會以日名稱初始化每個陣列元素：  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 當您在宣告時初始化陣列時，可以使用下列快速鍵：  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 您可以在不進行初始化的情況下宣告陣列變數，但必須在將陣列指派給變數時使用 `new` 運算子。 例如：  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 引進隱含型別陣列。 如需詳細資訊，請參閱[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。  
  
## <a name="value-type-and-reference-type-arrays"></a>實值型別和參考型別陣列

 請考慮下列陣列宣告：  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 此陳述式的結果取決於 `SomeType` 是實值型別還是參考型別。 如果它是實值型別，陳述式會建立 10 個項目的陣列，且每個都具有 `SomeType` 類型。 如果 `SomeType` 是參考型別，陳述式會建立 10 個項目的陣列，且每個都會初始化為 Null 參考。  
  
 如需實值型別和參考型別的詳細資訊，請參閱[類型](../../../csharp/language-reference/keywords/types.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Array>
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [陣列](../../../csharp/programming-guide/arrays/index.md)
- [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
