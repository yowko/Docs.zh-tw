---
title: 陣列 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715060"
---
# <a name="arrays-c-programming-guide"></a>陣列 (C# 程式設計手冊)

您可以在陣列資料結構中儲存相同類型的多個變數。 您可以指定陣列元素的類型來宣告陣列。 如果希望陣列存儲任何類型的元素，則可以指定`object`為其類型。 在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。

```csharp
type[] arrayName;
```

## <a name="example"></a>範例

下列範例會建立一維陣列、多維陣列和不規則陣列︰

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>陣列概述

陣列具有下列屬性︰

- 陣列可以是[一維](single-dimensional-arrays.md)、[多維](multidimensional-arrays.md)或[不規則](jagged-arrays.md)。
- 當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。 在執行個體的存留期期間，這些值無法變更。
- 數值陣列元素的預設值設定為零，且參考元素會設定為 null。
- 不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。
- 陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。
- 陣列元素可以是任何類型，包含陣列類型。
- 陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../language-reference/keywords/reference-types.md)。 由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../language-reference/keywords/foreach-in.md) 反覆項目。

## <a name="related-sections"></a>相關章節

- [陣列作為物件](arrays-as-objects.md)
- [搭配陣列使用 foreach](using-foreach-with-arrays.md)
- [傳遞陣列作為引數](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [集合](../concepts/collections.md)
