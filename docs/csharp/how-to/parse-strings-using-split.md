---
title: '使用字串來剖析字串。分割 (c # 指南) '
description: Split 方法會傳回從一組分隔符號分割的字串陣列。 它容易剖析字串。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: ee0921c4d3c931e2f677ec0bb8458992afc57d57
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342640"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>如何使用字串剖析字串。以 C 分隔\#

<xref:System.String.Split%2A?displayProperty=nameWithType> 方法會根據一或多個分隔符號來分割輸入字串，以建立子字串陣列。 這種方法通常是在單字邊界上分隔字串的最簡單方式。 它也可用來將字串分割成其他特定字元或字串。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下列程式碼將常用詞語分割成每個字組的字串陣列。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

每個分隔符號字元執行個體都會產生已傳回陣列中的值。 連續分隔符號字元會產生空字串，作為已傳回陣列中的值。 您可以在下列範例中看到如何建立空字串，此範例會使用空白字元做為分隔符號。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

這種行為可讓您更輕鬆地格式，像是逗號分隔值 (CSV) 代表表格式資料的檔案。 連續的逗號表示空白資料行。

您可以傳遞選擇性 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 參數，以排除已傳回陣列中的任何空字串。 針對更複雜處理的已傳回集合，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 來操作結果序列。

<xref:System.String.Split%2A?displayProperty=nameWithType> 可以使用多個分隔符號字元。
下列範例會使用空格、逗號、句號、冒號和定位點來分隔在陣列中傳遞給的字元 <xref:System.String.Split%2A> 。
程式碼底部的迴圈會顯示所傳回陣列中的每個字組。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

任何分隔符號的連續執行個體都會產生輸出陣列中的空字串：

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<xref:System.String.Split%2A?displayProperty=nameWithType> 可以採用字串陣列 (作為分隔符號以剖析目標字串的字元序列，而不是單一字元)。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a>另請參閱

- [從字串中解壓縮元素](../../standard/base-types/parse-strings.md)
- [C# 程式設計手冊](../programming-guide/index.md)
- [字串](../programming-guide/strings/index.md)
- [.NET 正則運算式](../../standard/base-types/regular-expressions.md)
