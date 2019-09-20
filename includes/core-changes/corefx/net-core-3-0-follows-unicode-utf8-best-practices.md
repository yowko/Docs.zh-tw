---
ms.openlocfilehash: 6643f64010332cf14d466cbba28a1c3cca671ac3
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117196"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3.0 在取代格式不正確的 UTF-8 位元組序列時，遵循 Unicode 最佳做法

<xref:System.Text.UTF8Encoding>當類別在位元組對字元轉碼作業期間遇到格式不正確的 utf-8 位元組序列時，它會將該序列取代為輸出字串中的 ' ' （U + FFFD 取代字元）字元。 .NET Core 3.0 與舊版 .NET Core 和 .NET Framework 的不同之處，是遵循在轉碼作業期間執行此取代的 Unicode 最佳作法。

這是改善整個 .net 的 utf-8 處理工作的一部分，包括新<xref:System.Text.Unicode.Utf8?displayProperty=nameWithType>的和<xref:System.Text.Rune?displayProperty=nameWithType>類型。 <xref:System.Text.UTF8Encoding>類型已獲得改善的錯誤處理機制，因此它會產生與新引進之類型一致的輸出。

#### <a name="details"></a>詳細資料

從 .net Core 3.0 開始，在將位元組轉換成字元<xref:System.Text.UTF8Encoding>時，類別會根據 Unicode 最佳做法執行字元替換。 使用的替代機制會在標題為_U + FFFD 替換為_[最大部分] 的標題中[，以12.0、秒3.9 （PDF）](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf)的形式加以描述。

只有當輸入位元組序列包含格式不正確的 UTF-8 資料時，_才_會套用此行為。 此外，如果<xref:System.Text.UTF8Encoding>已使用`throwOnInvalidBytes: true`來建立實例（請參閱 [UTF8Encoding 的處理常式`UTF8Encoding`檔]<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>（），實例會繼續在不正確輸入擲回，而不是執行 U + FFFD取代.

下圖說明這項變更與無效3位元組輸入的影響：

|3位元組輸入格式錯誤|.NET Core 3.0 之前的輸出|從 .NET Core 3.0 開始的輸出|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`（2個字元輸出）| `[ FFFD FFFD FFFD ]`（3個字元輸出）|

根據先前連結之 Unicode 標準 PDF 的_資料表 3-9_ ，這個3個字元的輸出是慣用的輸出。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

開發人員不需要採取任何動作。

#### <a name="category"></a>分類

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

