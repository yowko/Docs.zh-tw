---
title: 傳遞陣列當做引數 (C# 程式設計手冊)
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 0289297be9d7b4989cc95d2b50b92dae9ee831f7
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199219"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>傳遞陣列當做引數 (C# 程式設計手冊)

陣列可以作為引數傳遞至方法參數。 因為陣列是參考型別，所以方法可以變更項目的值。

## <a name="passing-single-dimensional-arrays-as-arguments"></a>傳遞一維陣列作為引數

您可以將初始化的一維陣列傳遞至方法。 例如，下列陳述式會將陣列傳送至列印方法。

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

下列程式碼顯示列印方法的部分實作。

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>範例

在下列範例中，字串的陣列會初始化，並作為引數傳遞至字串的 `DisplayArray` 方法。 此方法會顯示陣列的元素。 接下來，`ChangeArray` 方法會反轉陣列項目，然後 `ChangeArrayElements` 方法會修改陣列的前三個項目。 每個方法傳回之後，`DisplayArray` 方法會顯示以傳值方式傳遞陣列不會防止變更陣列元素。

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>傳遞多維陣列作為引數

將初始化的多維陣列傳遞至方法所使用的方式，與傳遞一維陣列的方式相同。

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

下列程式碼顯示可接受二維陣列作為其引數之列印方法的部分宣告。

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示：

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>範例

在下列範例中，整數的二維陣列會初始化並傳遞至 `Print2DArray` 方法。 此方法會顯示陣列的元素。

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>另請參閱

[C# 程式設計指南](../index.md)  
[陣列](index.md)  
[一維陣列](single-dimensional-arrays.md)  
[多維陣列](multidimensional-arrays.md)  
[不規則陣列](jagged-arrays.md)  