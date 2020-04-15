---
title: 如何變更字串內容 - C# 指南
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 8e9bbe76c689d3c3f9f238ca9dd95cc7fcf98b18
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389518"
---
# <a name="how-to-modify-string-contents-in-c"></a>如何變更 C 字串內容\#

本文示範多種技術，會藉由修改現有的 `string`來產生 `string`。 所有示範的技術均會傳回修改結果，作為新的 `string` 物件。 為明確示範此做法，所有的範例都會將結果儲存到新的變數。 接著，您可在執行各個範例時，對原本的 `string` 與修改後產生的 `string` 進行檢查。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

本文示範了多種技術。 您可以取代現有的文字。 您可以搜尋模式，並以其他文字取代相符的文字。 您可以將字串視為一串字元。 您也可以使用便利的方法來移除空白字元。 選擇與您的方案最匹配的技術。

## <a name="replace-text"></a>取代文字

下列程式碼會以替代項目取代現有文字，來建立新的字串。

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

上述程式碼示範了字串的「固定」** 屬性。 您可以看到在上述程式碼中，原本的字串 `source` 並未受到修改。 <xref:System.String.Replace%2A?displayProperty=nameWithType> 方法會建立包含修改項目的新 `string`。

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

規則運算式在搜尋及取代遵循模式的文字時相當實用，但對於已知文字則否。 關於詳細資訊,請參考[如何搜尋字串](search-strings.md)。 搜尋模式 "the\s" 會搜尋後面接著空白字元的字組 "the"。 模式的該部分會確認其不會對應來源字串中的 "there"。 如需規則運算式語言元素的詳細資訊，請參閱[規則運算式語言 - 快速參考](../../standard/base-types/regular-expression-language-quick-reference.md)。

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> 方法會傳回固定字串，其中包含 <xref:System.Text.StringBuilder> 物件中的內容。

## <a name="modifying-individual-characters"></a>修改個別字元

您可從字串產生字元陣列、修改陣列內容，然後從陣列中修改的內容建立新的字串。

下列範例示範了如何在字串中取代一組字元。 首先，使用 <xref:System.String.ToCharArray?displayProperty=nameWithType> 方法來建立字元陣列。 這會用到 <xref:System.String.IndexOf%2A> 方法來尋找字組 "fox" 的起始索引。 下三個字元會以不同字組取代。 最後，會從更新的字元陣列建構新字串。

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>以程式設計方式建構字串內容

由於字串是不可變的,前面的示例都創建臨時字串或字元陣列。 在高性能方案中,最好避免這些堆分配。 .NET Core<xref:System.String.Create%2A?displayProperty=nameWithType>提供了一種方法,允許您通過回調以程式設計方式填充字串的字元內容,同時避免中間臨時字串分配。

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

您可以使用不安全的程式碼修改固定塊中的字串,但**強烈建議**在創建字串後修改字串內容。 這樣做會以不可預知的方式破壞事情。 例如,如果有人實習生的內容與您的相同,他們會獲取您的副本,並且根本不希望您修改其字串。

您可以通過查看[GitHub 儲存庫](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)中的代碼來嘗試這些範例。 或者，您可以將範例下載[為 ZIP 檔案](../../../samples/snippets/csharp/how-to/strings.zip)。

## <a name="see-also"></a>另請參閱

- [.NET Framework 規則運算式](../../standard/base-types/regular-expressions.md)
- [規則運算式語言 - 快速參考](../../standard/base-types/regular-expression-language-quick-reference.md)
