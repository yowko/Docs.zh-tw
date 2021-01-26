---
title: 陣列 - C# 程式設計手冊
description: '在 c # 的陣列資料結構中儲存相同類型的多個變數。 藉由指定類型或指定物件來儲存任何類型來宣告陣列。'
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794773"
---
# <a name="arrays-c-programming-guide"></a>陣列 (C# 程式設計手冊)

您可以在陣列資料結構中儲存相同類型的多個變數。 您可以指定陣列元素的類型來宣告陣列。 如果您希望陣列儲存任何類型的元素，您可以指定 `object` 做為其類型。 在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。

```csharp
type[] arrayName;
```

## <a name="example"></a>範例

下列範例會建立一維陣列、多維陣列和不規則陣列︰

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>陣列總覽

陣列具有下列屬性︰

- 陣列可以是[單一維度](single-dimensional-arrays.md) [、多維度或](multidimensional-arrays.md)[不規則](jagged-arrays.md)的。
- 當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。 在執行個體的存留期期間，這些值無法變更。
- 數值陣列元素的預設值設定為零，且參考元素會設定為 null。
- 不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。
- 陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。
- 陣列元素可以是任何類型，包含陣列類型。
- 陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../language-reference/keywords/reference-types.md)。 由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../language-reference/keywords/foreach-in.md) 反覆項目。

### <a name="arrays-as-objects"></a>陣列作為物件

在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。 <xref:System.Array> 是所有陣列類型的抽象基底類型。 您可以使用具有的屬性和其他類別成員 <xref:System.Array> 。 其中一個範例是使用 <xref:System.Array.Length%2A> 屬性來取得陣列的長度。 下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。 下列範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>另請參閱

- [如何使用一維陣列](single-dimensional-arrays.md)
- [如何使用多維度陣列](multidimensional-arrays.md)
- [如何使用不規則陣列](jagged-arrays.md)
- [搭配陣列使用 foreach](using-foreach-with-arrays.md)
- [傳遞陣列作為引數](passing-arrays-as-arguments.md)
- [隱含類型陣列](implicitly-typed-arrays.md)
- [C # 程式設計指南](../index.md)
- [集合](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
