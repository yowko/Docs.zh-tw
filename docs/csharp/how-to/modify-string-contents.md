---
title: '如何修改字串內容-c # 指南'
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: e607a8a2e96a73f64463d75a75a2bfe3f518d118
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324161"
---
# <a name="how-to-modify-string-contents-in-c"></a>如何在 C 中修改字串內容\#

本文示範多種技術，會藉由修改現有的 `string`來產生 `string`。 所有示範的技術均會傳回修改結果，作為新的 `string` 物件。 為了示範原始和修改過的字串是相異的實例，這些範例會將結果儲存在新的變數中。 `string` `string` 當您執行每個範例時，您可以檢查原始的和新的。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

本文示範了多種技術。 您可以取代現有的文字。 您可以搜尋模式，並以其他文字取代相符的文字。 您可以將字串視為一串字元。 您也可以使用便利的方法來移除空白字元。 選擇最符合您案例的技術。

## <a name="replace-text"></a>取代文字

下列程式碼會以替代項目取代現有文字，來建立新的字串。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet1":::

上述程式碼示範了字串的「固定」** 屬性。 您可以看到在上述程式碼中，原本的字串 `source` 並未受到修改。 <xref:System.String.Replace%2A?displayProperty=nameWithType> 方法會建立包含修改項目的新 `string`。

<xref:System.String.Replace%2A> 方法可取代字串或單一字元。 在這兩種情況下，所找到之文字的每個項目均會受到取代。  下列範例將所有 ' ' 字元取代為 '\_'：

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet2":::

來源字串不會變更，而會傳回附帶取代項目的新字串。

## <a name="trim-white-space"></a>修剪空白字元

您可使用 <xref:System.String.Trim%2A?displayProperty=nameWithType>、<xref:System.String.TrimStart%2A?displayProperty=nameWithType> 及 <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> 方法來移除所有開頭和結尾的空白字元。  下列程式碼將示範各項作業。 來源字串不會變更，這些方法會傳回附帶已修改內容的新字串。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet3":::

## <a name="remove-text"></a>移除文字

您可使用 <xref:System.String.Remove%2A?displayProperty=nameWithType> 方法來移除字串中的文字。 此方法會從特定索引開始移除一些數字。 下列範例示範了如何在 <xref:System.String.IndexOf%2A?displayProperty=nameWithType> 後面使用 <xref:System.String.Remove%2A> 來移除字串文字：

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet4":::

## <a name="replace-matching-patterns"></a>取代相符的模式

您可使用[規則運算式](../../standard/base-types/regular-expressions.md)以新文字取代文字相符模式，可由模式定義。 下列範例使用 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別在來源字串中尋找模式，並以適當的大小寫加以取代。 <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> 方法會以提供取代項目邏輯的函式作為其引數之一。 在此範例中，該函式 `LocalReplaceMatchCase` 是在範例方法中宣告的**區域函式**。 `LocalReplaceMatchCase` 會使用 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別以適當的大小寫來建置取代字串。

規則運算式在搜尋及取代遵循模式的文字時相當實用，但對於已知文字則否。 如需詳細資訊，請參閱[如何搜尋字串](search-strings.md)。 搜尋模式 "the\s" 會搜尋後面接著空白字元的字組 "the"。 模式的該部分會確認其不會對應來源字串中的 "there"。 如需規則運算式語言元素的詳細資訊，請參閱[規則運算式語言 - 快速參考](../../standard/base-types/regular-expression-language-quick-reference.md)。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet5":::

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> 方法會傳回固定字串，其中包含 <xref:System.Text.StringBuilder> 物件中的內容。

## <a name="modifying-individual-characters"></a>修改個別字元

您可從字串產生字元陣列、修改陣列內容，然後從陣列中修改的內容建立新的字串。

下列範例示範了如何在字串中取代一組字元。 首先，使用 <xref:System.String.ToCharArray?displayProperty=nameWithType> 方法來建立字元陣列。 這會用到 <xref:System.String.IndexOf%2A> 方法來尋找字組 "fox" 的起始索引。 下三個字元會以不同字組取代。 最後，會從更新的字元陣列建構新字串。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet6":::

## <a name="programmatically-build-up-string-content"></a>以程式設計方式建立字串內容

由於字串是不可變的，因此先前的範例全都會建立暫存字串或字元陣列。 在高效能案例中，可能需要避免這些堆積配置。 .NET Core 提供了一 <xref:System.String.Create%2A?displayProperty=nameWithType> 種方法，可讓您透過回呼以程式設計方式填滿字串的字元內容，同時避免中繼暫存字串配置。

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet7":::

您可以使用 unsafe 程式碼修改固定區塊中的字串，但**強烈**建議您在建立字串之後修改字串內容。 這麼做會以無法預期的方式來中斷專案。 例如，如果有人實習一個具有與您相同內容的字串，他們會取得您的複本，而且不會預期您要修改其字串。

## <a name="see-also"></a>另請參閱

- [.NET Framework 正則運算式](../../standard/base-types/regular-expressions.md)
- [正則運算式語言-快速參考](../../standard/base-types/regular-expression-language-quick-reference.md)
