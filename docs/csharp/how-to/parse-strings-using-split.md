---
title: '如何使用字串剖析字串（c # 指南）'
description: String.Split 會傳回從一組分隔符號分割的字串陣列。 它容易剖析字串。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 4f0056426fb29ec3d76093e57fa45e2046f27a4f
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662988"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>如何使用字串來剖析字串。在 C 中分割\#

<xref:System.String.Split%2A?displayProperty=nameWithType> 方法會根據一或多個分隔符號來分割輸入字串，以建立子字串陣列。 這通常是分隔字組界限上字串的最簡單方式。 它也用來分割其他特定字元或字串上的字串。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下列程式碼將常用詞語分割成每個字組的字串陣列。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

每個分隔符號字元執行個體都會產生已傳回陣列中的值。 連續分隔符號字元會產生空字串，作為已傳回陣列中的值。 在下列範例中，您可以看到空字串的建立方式，其使用空白字元做為分隔符號。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

這種行為可讓格式類似逗號分隔值（CSV）檔案（代表表格式資料）變得更容易。 連續的逗號表示空白資料行。

您可以傳遞選擇性 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 參數，以排除已傳回陣列中的任何空字串。 針對更複雜處理的已傳回集合，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 來操作結果序列。

<xref:System.String.Split%2A?displayProperty=nameWithType> 可以使用多個分隔符號字元。
下列範例會使用空格、逗號、句號、冒號和定位點，全部以包含這些分隔符號的陣列傳遞至 <xref:System.String.Split%2A>。
程式碼底部的迴圈會顯示所傳回陣列中的每個字組。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

任何分隔符號的連續執行個體都會產生輸出陣列中的空字串：

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<xref:System.String.Split%2A?displayProperty=nameWithType> 可以採用字串陣列 (作為分隔符號以剖析目標字串的字元序列，而不是單一字元)。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../programming-guide/index.md)
- [字串](../programming-guide/strings/index.md)
- [.NET 正則運算式](../../standard/base-types/regular-expressions.md)
