---
ms.openlocfilehash: 70b71fc55f76514dd17e5b9ba0e76151a966eebb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539447"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>System.globalization.stringinfo> 和 TextElementEnumerator 現在已 UAX29 相容

在此變更之前，不會 <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> 正確處理所有語素簇叢集。 有些 graphemes 已分割成其組成元件，而不是保持在一起。 現在， <xref:System.Globalization.StringInfo> 並 <xref:System.Globalization.TextElementEnumerator> 根據 Unicode 標準的最新版本處理語素簇叢集。

此外，方法會將 <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 字串中的字元反轉 Visual Basic，現在也會遵循語素簇叢集的 Unicode 標準。

#### <a name="change-description"></a>變更描述

[語素簇](https://www.unicode.org/glossary/#grapheme)或[extended 語素簇](https://www.unicode.org/glossary/#extended_grapheme_cluster)叢集是由多個 Unicode 程式碼點組成的單一使用者感知字元。 例如，包含泰文字元 "kam" (:::no-loc text="กำ":::) 包含下列兩個字元的字串：

- :::no-loc text="ก"::: (= ' \u0e01 ' ) 泰文字元 KO KAI
- :::no-loc text=" ำ"::: (= ' \u0e33 ' ) 泰文字元 SARA AM

向使用者顯示時，作業系統會結合兩個字元來形成單一顯示字元 (或語素簇) "kam" 或 :::no-loc text="กำ"::: 。 表情也可以包含多個合併以供顯示的字元。

> [!TIP]
> .NET 檔在參考語素簇時，有時會使用「文字元素」一詞。

<xref:System.Globalization.StringInfo>和 <xref:System.Globalization.TextElementEnumerator> 類別會檢查字串，並傳回它們所包含之 graphemes 的相關資訊。 在 .NET Framework () 和 .NET Core 3.x 及更早版本的所有版本，這兩個類別會使用自訂邏輯來處理一些合併類別，但不完全符合 [Unicode 標準](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)。 例如， <xref:System.Globalization.StringInfo> 和類別會 <xref:System.Globalization.TextElementEnumerator> 錯誤地將單一泰文字元 "kam" 分割回其構成元件，而不是將它們保持在一起。 這些類別也會錯誤地將表情字元 "🤷🏽♀️" 分割成四個叢集 (person shrugging、膚色修飾詞、性別修飾詞和不可見的結合器) ，而不是將它們保持在一起成為單一語素簇叢集。

從 .NET 5 開始， <xref:System.Globalization.StringInfo> 和類別會依照 <xref:System.Globalization.TextElementEnumerator> [unicode 標準附錄 \# 29、rev. 35、sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html)的定義來執行 unicode 標準。 尤其是，它們現在會傳回所有合併類別的 [擴充語素簇](https://www.unicode.org/glossary/#extended_grapheme_cluster) 叢集。

請考慮下列 c # 程式碼：

```csharp
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

在 .NET Framework 和 .NET Core 3.x 及更早版本中，graphemes 會進行分割，主控台輸出如下所示：

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

在 .NET 5 和更新版本中，graphemes 會保持在一起，而主控台輸出如下所示：

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

此外，從 .NET 5 開始，方法會將 <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 字串中的字元反轉 Visual Basic 的 Unicode 標準，現在也會遵循語素簇叢集的 Unicode 標準。

這些變更是 .NET 中一組更廣泛的 Unicode 和 UTF-8 增強功能的一部分，包括擴充的語素簇叢集列舉 API，以補充 <xref:System.Text.Rune?displayProperty=fullName> .Net Core 3.0 中的類型所引進的 unicode 純量值列舉 api。

#### <a name="version-introduced"></a>引進的版本

.NET 5.0 Preview 1

#### <a name="recommended-action"></a>建議的動作

您不需要採取任何動作。 在各種全球化相關案例中，您的應用程式會以更符合標準的方式自動運作。

#### <a name="category"></a>類別

全球化

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
