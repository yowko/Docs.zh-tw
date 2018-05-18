---
title: 如何：串連多個字串 (C# 指南)
description: 以下提供用 C# 串連字串的多種方式。 了解選項及做出不同選擇的原因。
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: d4e57347a11b804f3ea7f4bb9736c134c4b71929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>如何：串連多個字串 (C# 指南)

「串連」是將一個字串附加至另一個字串結尾的程序。 使用 `+` 運算子即可串連字串。 若是字串常值和字串常數，會在編譯時間進行串連；在非編譯時間不會發生串連。 若是字串變數，串連只會發生在執行階段。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下例使用串連將長字串常值分割成較小的字串，以改善原始程式碼的可讀性。 這些組件在編譯時期會串連成單一字串。 不論範圍涵蓋多少字串，都不會產生執行階段效能成本。  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

若要串連字串變數，您可以使用 `+` 或 `+=` 運算子、[字串內插補點](../language-reference/tokens/interpolated.md)，或是 <xref:System.String.Format%2A?displayProperty=nameWithType>、<xref:System.String.Concat%2A?displayProperty=nameWithType>、<xref:System.String.Join%2A?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> 方法。 `+` 運算子簡單易用，且容易建立直覺化程式碼。 即使一個陳述式使用數個 `+` 運算子，字串內容也只會複製一次。 下列程式碼示範使用 `+` 和 `+=` 運算子來串連字串的範例：

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

在某些運算式中，使用字串內插補點會更容易串連字串，如下列程式碼所示：
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  在字串串連作業中，C# 編譯器會將 null 字串視同空字串。

<xref:System.String.Format%2A?displayProperty=nameWithType> 也是串連字串的方法。 當您從少量元件字串建置字串時，此方法能順利執行。

在其他情況下，您可能要結合迴圈中的字串，但您不知道要結合的來源字串數是多少，而且實際來源字串數可能非常大。 <xref:System.Text.StringBuilder> 類別專為這種案例而設計。 下列程式碼會使用 <xref:System.Text.StringBuilder> 類別的 <xref:System.Text.StringBuilder.Append%2A> 方法來串連字串。  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

您可以閱讀更多內容，了解[選擇字串串連或 `StringBuilder` 類別的原因](xref:System.Text.StringBuilder#StringAndSB)

從集合加入字串的另一個選項是使用 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法。 如果應該以分隔符號分隔來源字串，請使用 <xref:System.String.Join%2A?displayProperty=nameWithType> 方法。 下列程式碼會使用這兩種方法來結合文字陣列：

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

最後，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 和 <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> 方法從集合加入字串。 這個方法使用 Lambda 運算式結合來源字串。 Lambda 運算式會負責將各個字串新增到目前累積的內容。 下列範例透過在陣列中的每個字之間新增空格，結合一個陣列的字組：

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

您可以查看 [GitHub 存放庫](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)中的程式碼，來嘗試這些範例。 或者，您可以將範例下載[為 ZIP 檔案](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)。

## <a name="see-also"></a>請參閱  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [C# 程式設計指南](../programming-guide/index.md)  
 [字串](../programming-guide/strings/index.md)
