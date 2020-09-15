---
ms.openlocfilehash: 48d2f1b5fa2eced30d3c9fb65804268904f11ab8
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065056"
---
### <a name="unicode-category-changed-for-some-latin-1-characters"></a>某些拉丁字元的 Unicode 類別已變更

<xref:System.Char> 方法現在會針對拉丁-1 範圍中的字元傳回正確的 Unicode 分類。 類別符合 Unicode 標準的類別。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中， <xref:System.Char> 方法會使用 Unicode 分類的固定清單來代表拉丁-1 範圍中的字元。 不過，Unicode 標準已經變更這些字元的類別，因為這些是這些字元都已實作為這些字元，所以會產生差異。 此外，與 api 之間的差異也會 <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> 遵循 Unicode 標準。 在 .NET 5.0 和更新版本中， <xref:System.Char> 方法會使用並傳回符合所有字元 unicode 標準的 unicode 分類。

下表顯示其 Unicode 類別在 .NET 5.0 中已變更的字元：

| 字元    | Unicode 類別<br>在先前的 .NET 版本中 | Unicode 類別<br>.NET 5.0 和更新版本中的 |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| § ( \u00a7)    | `OtherSymbol`                                 | `OtherPunctuation`                                 |
|  ( 的 \u00aa)    | `LowercaseLetter`                             | `OtherLetter`                                      |
| SHY ( \u00ad)  | `DashPunctuation`                             | `Format`                                           |
| ¶ ( \u00b6)    | `OtherSymbol`                                 | `OtherPunctuation`                                 |
|  ( \u00ba)    | `LowercaseLetter`                             | `OtherLetter`                                      |

#### <a name="version-introduced"></a>引進的版本

.NET 5.0 RC1

#### <a name="recommended-action"></a>建議的動作

如果您有任何程式碼使用類別取得 Unicode 字元類別， <xref:System.Char> 並假設類別永遠不會變更，您可能需要更新它。

#### <a name="reason-for-change"></a>變更的原因

這項變更是為了讓類型所傳回的類別 <xref:System.Char> 與 Unicode 標準和 <xref:System.Globalization.CharUnicodeInfo> 類型一致。

#### <a name="category"></a>類別

- Core .NET 程式庫
- 全球化

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

此外，任何依賴 <xref:System.Char> 來取得 Unicode 字元類別目錄的類別（例如） <xref:System.Text.RegularExpressions.Regex> 都會受到這項變更的影響。

<!--

#### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

-->
