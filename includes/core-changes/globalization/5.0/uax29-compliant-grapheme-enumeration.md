---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888162"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo 與文字元素的手舉器現在符合 UAX29 標準

在此更改之前,<xref:System.Globalization.StringInfo?displayProperty=fullName><xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>並沒有 正確處理所有石墨星系團。 一些石墨烯被分割成其組成成分,而不是放在一起。 現在,<xref:System.Globalization.StringInfo>並<xref:System.Globalization.TextElementEnumerator>根據最新版本的 Unicode 標準處理石墨組。

此外,<xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>該方法在 Visual Basic 中反轉字串中的字元,現在也遵循圖目組中的 Unicode 標準。

#### <a name="change-description"></a>變更描述

[圖目或](https://www.unicode.org/glossary/#grapheme)[擴展圖目組](https://www.unicode.org/glossary/#extended_grapheme_cluster)是單個使用者感知的字元,可能由多個 Unicode 代碼點組成。 例如,包含泰語字元「kam」:::no-loc text="กำ":::( ) 的字串由以下兩個字元組成:

- :::no-loc text="ก":::(= "\u0e01")泰語人物 KO KAI
- :::no-loc text=" ำ":::(= "\u0e33")泰國字元 SARA AM

將使用者顯示時,作業系統會兩個字符合並,以形成單個顯示字元(或石墨)"kam'或:::no-loc text="กำ":::。 表情符號還可以由多個字元組成,這些字元組合起來以類似方式顯示。

> [!TIP]
> .NET 文件有時在引用石墨時使用術語"文本元素"。

<xref:System.Globalization.StringInfo>和<xref:System.Globalization.TextElementEnumerator>類檢查字串並返回有關它們包含的圖目關係的資訊。 在 .NET 框架 (所有版本)和 .NET Core 3.x 及更早版本中,這兩個類使用自訂邏輯來處理某些組合類,但並不完全符合[Unicode 標準](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)。 例如,<xref:System.Globalization.StringInfo><xref:System.Globalization.TextElementEnumerator>和 類錯誤地將單個泰語字元"kam"拆分回其組成元件,而不是將它們保留在一起。 這些類還錯誤地將表情符號字元「🤷🏽♀️」拆分為四個群集(人聳肩、膚色修飾器、性別修飾符和不可見的組合器),而不是將它們作為單個圖形學聚類保留在一起。

從 .NET<xref:System.Globalization.StringInfo><xref:System.Globalization.TextElementEnumerator>5 開始 ,和 類別實現 Unicode 標準定義的 Unicode 標準,由[Unicode\#標準附件 29,第 35,第 3 秒 。](https://www.unicode.org/reports/tr29/tr29-35.html) 特別是,它們現在返回所有組合類的[擴展石墨姆群集](https://www.unicode.org/glossary/#extended_grapheme_cluster)。

請考慮以下 C# 程式碼:

```cs
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

在 .NET 框架和 .NET Core 3.x 和早期版本中,圖形圖姆被拆分,控制台輸出如下所示:

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

在 .NET 5 和更高版本中,圖目數保持在一起,控制台輸出如下所示:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

此外,從 .NET<xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>5 開始 ,該方法在 Visual Basic 中反轉字串中的字元,現在也遵循圖目組中的 Unicode 標準。

這些更改是 .NET 中更廣泛的 Unicode 和 UTF-8 改進集的一部分,包括擴展的圖目組枚舉 API,以補充使用<xref:System.Text.Rune?displayProperty=fullName>.NET Core 3.0 中的類型引入的 Unicode scalar 值枚舉 API。

#### <a name="version-introduced"></a>介紹的版本

.NET 5.0 預覽 1

### <a name="recommended-action"></a>建議的動作

您不需要採取任何動作。 在各種與全球化相關的方案中,您的應用將自動以更符合標準的方式運行。

### <a name="category"></a>類別

全球化

### <a name="affected-apis"></a>受影響的 API

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
