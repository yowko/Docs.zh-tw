---
title: 陣列 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e0ed2d678363a29bb870a496846fc6f054769a4b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46530072"
---
# <a name="arrays-c-programming-guide"></a>陣列 (C# 程式設計手冊)

您可以在陣列資料結構中儲存相同類型的多個變數。 您可以指定陣列元素的類型來宣告陣列。  
  
 `type[] arrayName;`  
  
 下列範例會建立一維陣列、多維陣列和不規則陣列︰  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a>陣列概觀

 陣列具有下列屬性︰  
  
-   陣列可以是[一維](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多維](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)或[不規則](../../../csharp/programming-guide/arrays/jagged-arrays.md)。  
  
-   當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。 在執行個體的存留期期間，這些值無法變更。  
  
-   數值陣列元素的預設值設定為零，且參考元素會設定為 null。  
  
-   不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。  
  
-   陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。  
  
-   陣列元素可以是任何類型，包含陣列類型。  
  
-   陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../../csharp/language-reference/keywords/reference-types.md)。 由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反覆項目。  
  
## <a name="related-sections"></a>相關章節  
  
-   [陣列作為物件](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [搭配陣列使用 foreach](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [傳遞陣列作為引數](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>C# 語言規格

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [集合](../../../csharp/programming-guide/concepts/collections.md)  
- [Array 集合類型 (英文)](https://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
