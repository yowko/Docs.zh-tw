---
title: 如何使用 String.Split(C# 指南)分析字串
description: String.Split 會傳回從一組分隔符號分割的字串陣列。 它容易剖析字串。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: cf8307517213b54041b272843232eb595660b2e9
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389510"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>如何使用 String.分割在 C 中分析字串\#

<xref:System.String.Split%2A?displayProperty=nameWithType> 方法會根據一或多個分隔符號來分割輸入字串，以建立子字串陣列。 這通常是分隔字組界限上字串的最簡單方式。 它也用來分割其他特定字元或字串上的字串。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下列程式碼將常用詞語分割成每個字組的字串陣列。

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

每個分隔符號字元執行個體都會產生已傳回陣列中的值。 連續分隔符號字元會產生空字串，作為已傳回陣列中的值。 您可以在下面的範例中查看如何建立空字串,該示例使用空格字元作為分隔符。

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

此行為使表示表格數據的逗號分隔值 (CSV) 檔等格式更容易。 連續的逗號表示空白資料行。

您可以傳遞選擇性 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 參數，以排除已傳回陣列中的任何空字串。 針對更複雜處理的已傳回集合，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 來操作結果序列。

<xref:System.String.Split%2A?displayProperty=nameWithType> 可以使用多個分隔符號字元。
下列範例會使用空格、逗號、句號、冒號和定位點，全部以包含這些分隔符號的陣列傳遞至 <xref:System.String.Split%2A>。
程式碼底部的迴圈會顯示所傳回陣列中的每個字組。  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

任何分隔符號的連續執行個體都會產生輸出陣列中的空字串：

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> 可以採用字串陣列 (作為分隔符號以剖析目標字串的字元序列，而不是單一字元)。  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

您可以通過查看[GitHub 儲存庫](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)中的代碼來嘗試這些範例。 或者，您可以將範例下載[為 ZIP 檔案](../../../samples/snippets/csharp/how-to/strings.zip)。

## <a name="see-also"></a>另請參閱

- [C# 編程指南](../programming-guide/index.md)
- [字串](../programming-guide/strings/index.md)
- [.NET 規則運算式](../../standard/base-types/regular-expressions.md)
