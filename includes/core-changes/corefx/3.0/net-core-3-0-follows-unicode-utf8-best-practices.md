---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032030"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a>取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針

當 <xref:System.Text.UTF8Encoding> 類別在位元組對字元轉碼作業期間遇到格式不正確的 utf-8 位元組序列時，會以輸出字串中的 ' ' (U + FFFD 取代字元) 字元來取代該序列。 .NET Core 3.0 與舊版的 .NET Core 和 .NET Framework 有不同之處，就是遵循在轉碼作業期間執行此取代的 Unicode 最佳做法。

這是改善整個 .NET 的 UTF-8 處理工作的一部分，包括新的 <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> 和 <xref:System.Text.Rune?displayProperty=nameWithType> 類型。 此 <xref:System.Text.UTF8Encoding> 類型已獲得改良的錯誤處理機制，因此它會產生與新引進之類型一致的輸出。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始，當轉碼位元組到字元時， <xref:System.Text.UTF8Encoding> 類別會根據 Unicode 最佳作法執行字元替代。 使用的替代機制是以 [Unicode 標準12.0、Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) 的標題標題為 _U + FFFD 的最大子零件替代_。

只有當輸入位元組序列包含格式不正確的 UTF-8 資料時， _才_ 會套用此行為。 此外，如果 <xref:System.Text.UTF8Encoding> 已使用來建立實例 `throwOnInvalidBytes: true` ， `UTF8Encoding` 實例會繼續擲回不正確輸入，而不是執行 U + FFFD 取代。 如需有關此函數的詳細資訊 `UTF8Encoding` ，請參閱 <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> 。

下表說明這項變更的影響，以及不正確3位元組輸入：

| 3位元組格式錯誤的輸入 | .NET Core 3.0 之前的輸出          | 從 .NET Core 3.0 開始的輸出        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | `[ FFFD FFFD ]` (2-字元輸出)  | `[ FFFD FFFD FFFD ]` (3-字元輸出)  |

根據先前連結之 Unicode 標準 PDF 的 _表格 3-9_ ，3-char 輸出是慣用的輸出。

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
