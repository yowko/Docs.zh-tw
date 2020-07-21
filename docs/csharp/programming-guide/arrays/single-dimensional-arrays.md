---
title: 一維陣列 - C# 程式設計手冊
description: '使用 new 運算子，在 c # 中建立一維陣列，以指定陣列專案類型和元素數目。'
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474588"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>一維陣列 (C# 程式設計手冊)

您可以使用[new](../../language-reference/operators/new-operator.md)運算子來建立一維陣列，以指定陣列專案類型和元素數目。 下列範例會宣告五個整數的陣列：

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

這個陣列包含從 `array[0]` 到 `array[4]` 的項目。 陣列的元素會初始化為整數的元素類型的預設值 `0` 。

陣列可以儲存您指定的任何元素類型，例如下列宣告字串陣列的範例：

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a>陣列初始化

當您宣告陣列時，您可以初始化陣列的元素。 長度規範不是必要的，因為它是由初始化清單中的元素數目所推斷。 例如：

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

下列程式碼顯示字串陣列的宣告，其中每個陣列專案都是以一天的名稱初始化：

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
當您在宣告 `new` 時初始化陣列時，可以避免運算式和陣列類型，如下列程式碼所示。 這稱為[隱含類型陣列](implicitly-typed-arrays.md)：

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

您可以宣告陣列變數而不建立它，但 `new` 當您將新陣列指派給這個變數時，必須使用運算子。 例如：

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a>實值型別和參考型別陣列

請考慮下列陣列宣告：  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

此陳述式的結果取決於 `SomeType` 是實值型別還是參考型別。 如果它是實值型別，則語句會建立10個專案的陣列，其中每個專案都有型別 `SomeType` 。 如果 `SomeType` 是參考型別，陳述式會建立 10 個項目的陣列，且每個都會初始化為 Null 參考。 在這兩個實例中，專案都會初始化為元素類型的預設值。 如需實數值型別和參考型別的詳細資訊，請參閱實[數值型別](../../language-reference/builtin-types/value-types.md)和[參考型別](../../language-reference/keywords/reference-types.md)。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Array>
- [陣列](./index.md)
- [多維陣列](./multidimensional-arrays.md)
- [不規則陣列](./jagged-arrays.md)
