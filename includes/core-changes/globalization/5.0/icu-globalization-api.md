---
ms.openlocfilehash: 02b5dc181abe384c1a5f47c042e475f67a0afe1c
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400798"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a>全球化 Api 在 Windows 上使用 ICU 程式庫

.NET 5.0 和更新版本會在 Windows 10 2019 年5月更新或更新版本上執行時，使用 [Unicode (ICU) ](http://site.icu-project.org/home) 程式庫的全球化功能。

#### <a name="change-description"></a>變更描述

在 .NET Core 1.0-3.1 和 .NET Framework 4 和更新版本中，.NET 程式庫使用 [國家語言支援 (NLS) ](/windows/win32/intl/national-language-support) api，在 Windows 上提供全球化功能。 例如，NLS 函數是用來比較字串、取得文化特性資訊，以及在適當的文化特性中執行字串大小寫。

從 .NET 5.0 開始，如果應用程式在 Windows 10 2019 年5月更新或更新版本上執行，則 .NET 程式庫預設會使用 [ICU](http://site.icu-project.org/home) 全球化 api。

> [!NOTE]
> Windows 10 2019 年5月更新和更新版本隨附于 ICU 原生程式庫。 如果 .NET 執行時間無法載入 ICU，則會改為使用 NLS。

#### <a name="behavioral-differences"></a>行為差異

即使您不知道您使用的是全球化設施，您也可能會在應用程式中看到變更。 本節列出您可能會看到的一些行為變更，但也有其他的行為變更。

##### <a name="stringindexof"></a>String.IndexOf

請考慮下列程式碼，該程式碼會呼叫 <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> 以找出字串中分行符號的索引。

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- 在舊版的 Windows 中，程式碼片段會列印出來 `6` 。
- 在 Windows 19H1 和更新版本的 .NET 5.0 和更新版本中，程式碼片段會列印 `-1` 。

若要藉由執行序數搜尋而不是區分文化特性的搜尋來修正此程式碼，請呼叫多載 <xref:System.String.IndexOf(System.String,System.StringComparison)> ，並傳入 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 做為引數。

您可以執行程式碼分析規則 [CA1307：為清楚起見指定 StringComparison](../../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) ，以及 [CA1309：使用序數 StringComparison](../../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) ，在您的程式碼中尋找這些呼叫位置。

如需詳細資訊，請參閱在 [.net 5 + 上比較字串時的行為變更](../../../../docs/standard/base-types/string-comparison-net-5-plus.md)。

##### <a name="currency-symbol"></a>貨幣符號

請考慮使用貨幣格式規範來格式化字串的下列程式碼 `C` 。 目前線程的文化特性設定為僅包含語言的文化特性，而不是國家/地區。

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- 在舊版的 Windows 中，文字的值為 `"100,00 €"` 。
- 在 Windows 19H1 和更新版本的 .NET 5.0 和更新版本中，文字的值是 `"100,00 ¤"` ，它會使用國際貨幣符號而非歐元。 在 ICU 中，設計是貨幣是國家或地區的屬性，不是語言。

#### <a name="reason-for-change"></a>變更的原因

這是為了統一而引進的變更。在所有支援的作業系統上的淨全球化行為。 它也能讓應用程式組合自己的全球化程式庫，而不需要依賴作業系統的內建程式庫。

#### <a name="version-introduced"></a>引進的版本

.NET 5.0 Preview 4

#### <a name="recommended-action"></a>建議的動作

開發人員不需要採取任何動作。 但是，如果您想要繼續使用 NLS 全球化 Api，您可以將 [執行時間參數](../../../../docs/core/run-time-config/globalization.md#nls) 設定為還原為該行為。 如需可用參數的詳細資訊，請參閱 [.net 全球化和 ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) 文章。

#### <a name="category"></a>類別

- Core .NET 程式庫
- 全球化

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- 命名空間中的大部分類型 <xref:System.Globalization?displayProperty=fullName>
- <xref:System.Array.Sort%2A?displayProperty=fullName> 排序字串陣列時 () 
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> 當清單元素是字串時 () 
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> 當索引鍵為字串時 () 
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> 當索引鍵為字串時 () 
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> 當集合包含字串時 () 

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

-->
