---
title: "不規則陣列 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
caps.latest.revision: 24
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
ms.openlocfilehash: cb6c0823af37924235dba7daa20e607cb8402a79
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="jagged-arrays-c-programming-guide"></a>不規則陣列 (C# 程式設計手冊)
不規則陣列是一種陣列，其元素也是陣列。 不規則陣列的項目可以有不同的維度和大小。 不規則陣列有時稱為「陣列的陣列」。 下列範例示範如何宣告、初始化和存取不規則陣列。  
  
 下列是具有三個項目的一維陣列宣告，且每個都是整數的一維陣列：  
  
 [!code-cs[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 必須先初始化 `jaggedArray` 的項目，才能予以使用。 您可以初始化項目，如下所示：  
  
 [!code-cs[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 每個項目都是整數的一維陣列。 第一個項目是 5 個整數的陣列、第二個是 4 個整數的陣列，而第三個是 2 個整數的陣列。  
  
 也可以使用初始設定式將值填入陣列元素，在此情況下，您不需要陣列大小。 例如:   
  
 [!code-cs[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 您也可以在宣告時初始化陣列，如下所示：  
  
 [!code-cs[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 您可以使用下列簡短格式。 請注意，您不能從項目初始化省略 `new` 運算子，因為沒有項目的預設初始化：  
  
 [!code-cs[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。  
  
 您可以存取個別陣列元素，例如下列範例：  
  
 [!code-cs[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 可以混合使用不規則陣列與多維陣列。 以下是一維不規則陣列的宣告和初始化，而此陣列包含三個不同大小的二維陣列元素。 如需二維陣列的詳細資訊，請參閱[多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)。  
  
 [!code-cs[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 如此範例所示，您可以存取個別項目，其中會顯示第一個陣列的項目 `[1,0]` 值 (值 `5`)：  
  
 [!code-cs[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 `Length` 方法會傳回不規則陣列中所含的陣列數目。 例如，假設您已經宣告先前的陣列，如下行所示：  
  
 [!code-cs[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 會傳回值 3。  
  
## <a name="example"></a>範例  
 此範例會建置其項目本身為陣列的陣列。 每個陣列元素都會有不同的大小。  
  
 [!code-cs[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Array>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)

