---
title: 如何：修改字串內容 - C# 指南
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 99102fe90f5f675235e2993b7dd99f59214862d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-string-contents-in-c"></a>如何：在 C# 中修改字串內容 #

本文示範多種技術，會藉由修改現有的 `string`來產生 `string`。 所有示範的技術均會傳回修改結果，作為新的 `string` 物件。 為明確示範此做法，所有的範例都會將結果儲存到新的變數。 接著，您可在執行各個範例時，對原本的 `string` 與修改後產生的 `string` 進行檢查。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

本文示範了多種技術。 您可以取代現有的文字。 您可以搜尋模式，並以其他文字取代相符的文字。 您可以將字串視為一串字元。 您也可以使用便利的方法來移除空白字元。 您應該選擇最符合您案例的技術。

## <a name="replace-text"></a>取代文字

下列程式碼會以替代項目取代現有文字，來建立新的字串。

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

上述程式碼示範了字串的「固定」屬性。 您可以看到在上述程式碼中，原本的字串 `source` 並未受到修改。 <xref:System.String.Replace%2A?displayProperty=nameWithType> 方法會建立包含修改項目的新 `string`。

<xref:System.String.Replace%2A> 方法可取代字串或單一字元。 在這兩種情況下，所找到之文字的每個項目均會受到取代。  下列範例將所有 ' ' 字元取代為 '\_'：

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

來源字串不會變更，而會傳回附帶取代項目的新字串。

## <a name="trim-white-space"></a>修剪空白字元

您可使用 <xref:System.String.Trim%2A?displayProperty=nameWithType>、<xref:System.String.TrimStart%2A?displayProperty=nameWithType> 及 <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> 方法來移除所有開頭和結尾的空白字元。  下列程式碼將示範各項作業。 來源字串不會變更，這些方法會傳回附帶已修改內容的新字串。

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>移除文字

您可使用 <xref:System.String.Remove%2A?displayProperty=nameWithType> 方法來移除字串中的文字。 此方法會從特定索引開始移除一些數字。 下列範例示範了如何在 <xref:System.String.IndexOf%2A?displayProperty=nameWithType> 後面使用 <xref:System.String.Remove%2A> 來移除字串文字：

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>取代相符的模式

您可使用[規則運算式](../../standard/base-types/regular-expressions.md)以新文字取代文字相符模式，可由模式定義。 下列範例使用 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別在來源字串中尋找模式，並以適當的大小寫加以取代。 <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> 方法會以提供取代項目邏輯的函式作為其引數之一。 在此範例中，該函式 `LocalReplaceMatchCase` 是在範例方法中宣告的**區域函式**。 `LocalReplaceMatchCase` 會使用 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別以適當的大小寫來建置取代字串。

規則運算式在搜尋及取代遵循模式的文字時相當實用，但對於已知文字則否。 如需詳細資料，請參閱[如何：搜尋字串](search-strings.md)。 搜尋模式 "the\s" 會搜尋後面接著空白字元的字組 "the"。 模式的該部分會確認其不會對應來源字串中的 "there"。 如需規則運算式語言元素的詳細資訊，請參閱[規則運算式語言 - 快速參考](../../standard/base-types/regular-expression-language-quick-reference.md)。

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> 方法會傳回固定字串，其中包含 <xref:System.Text.StringBuilder> 物件中的內容。

## <a name="modifying-individual-characters"></a>修改個別字元

您可從字串產生字元陣列、修改陣列內容，然後從陣列中修改的內容建立新的字串。

下列範例示範了如何在字串中取代一組字元。 首先，使用 <xref:System.String.ToCharArray?displayProperty=nameWithName> 方法來建立字元陣列。 這會用到 <xref:System.String.IndexOf%2A> 方法來尋找字組 "fox" 的起始索引。 下三個字元會以不同字組取代。 最後，會從更新的字元陣列建構新字串。

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>對字串進行不安全的修改

您可在字串建立後，使用**不安全**的程式碼直接加以修改。 不安全的程式碼會略過許多 .NET 設計來減少程式碼中特定類型 Bug 的功能。 因為字串類別設計為**固定**類型，所以您必須使用不安全的程式碼才能直接修改字串。 建立後即無法變更其值。 不安全的程式碼會藉由存取及修改 `string` 使用的記憶體，而不使用一般 `string` 方式，以規避此屬性。
下列範例專為特殊情況提供，例如您想要使用不安全的模式來直接修改字串。 此範例示範了如何使用 `fixed` 關鍵字。 `fixed` 關鍵字會在程式碼使用不安全的指標存取記憶體時，禁止記憶體回收行程 (GC) 移動記憶體中的字串物件。 它也示範因為 C# 編譯器在內部儲存 (實習生) 字串的方式，可能造成的字串不安全作業的一個副作用。 一般情況下，除非絕對必要，您不應該使用這項技術。 您可從這邊文章深入了解 [unsafe](../language-reference/keywords/unsafe.md) 與 [fixed](../language-reference/keywords/fixed-statement.md)。 <xref:System.String.Intern%2A> 的 API 參考包含字串暫留的資訊。

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

您可以查看 [GitHub 存放庫](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)中的程式碼，來嘗試這些範例。 或者，您可以將範例下載[為 ZIP 檔案](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)。

## <a name="see-also"></a>另請參閱

[.NET Framework 規則運算式](../../standard/base-types/regular-expressions.md)  
 [規則運算式語言 - 快速參考](../../standard/base-types/regular-expression-language-quick-reference.md)  
