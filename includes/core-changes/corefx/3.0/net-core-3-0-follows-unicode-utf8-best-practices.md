---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721689"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a>取代格式不正確的 UTF-8 位元組序列遵循 Unicode 方針

當 <xref:System.Text.UTF8Encoding> 類別在位元組對字元轉碼作業期間遇到格式不正確的 utf-8 位元組序列時，它會以輸出字串中的 ' ' （U + FFFD 取代字元）字元取代該序列。 .NET Core 3.0 與舊版 .NET Core 和 .NET Framework 的不同之處，是遵循在轉碼作業期間執行此取代的 Unicode 最佳作法。

這是改善整個 .NET 的 UTF-8 處理工作的一部分，包括新的 <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> 和 <xref:System.Text.Rune?displayProperty=nameWithType> 類型。 <xref:System.Text.UTF8Encoding>類型已獲得改善的錯誤處理機制，因此它會產生與新引進之類型一致的輸出。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始，在將位元組轉換成字元時， <xref:System.Text.UTF8Encoding> 類別會根據 Unicode 最佳做法執行字元替換。 使用的替代機制會在標題為_U + FFFD 替換為_[最大部分] 的標題中[，以12.0、秒3.9 （PDF）](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf)的形式加以描述。

只有當輸入位元組序列包含格式不正確的 UTF-8 資料時，_才_會套用此行為。 此外，如果實例是使用所建立 <xref:System.Text.UTF8Encoding> `throwOnInvalidBytes: true` ，則 `UTF8Encoding` 實例會繼續在不正確輸入中擲回，而不是執行 U + FFFD 取代。 如需有關此函數的詳細資訊 `UTF8Encoding` ，請參閱 <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> 。

下表說明此變更與無效3位元組輸入的影響：

| 3位元組輸入格式錯誤 | .NET Core 3.0 之前的輸出          | 從 .NET Core 3.0 開始的輸出        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | `[ FFFD FFFD ]`（2個字元輸出） | `[ FFFD FFFD FFFD ]`（3個字元輸出） |

根據先前連結之 Unicode 標準 PDF 的_資料表 3-9_ ，3個字元的輸出是慣用的輸出。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

開發人員不需要採取任何動作。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
