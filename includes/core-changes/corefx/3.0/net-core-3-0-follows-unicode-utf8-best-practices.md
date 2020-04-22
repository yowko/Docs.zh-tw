---
ms.openlocfilehash: 843c78bb4e4f88d9ac58308a91ab8278364c9580
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021648"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3.0 在取代格式錯誤的 UTF-8 位元組序列時遵循 Unicode 最佳實作

當類<xref:System.Text.UTF8Encoding>在位元組到字元轉碼操作期間遇到格式錯誤的 UTF-8 位元組序列時,它將在輸出字串中用''(U+FFFD 替換字元)替換該序列。 .NET Core 3.0 不同於早期版本的 .NET Core 和 .NET Framework,在轉碼操作期間遵循 Unicode 最佳做法執行此替換。

這是改進整個 .NET 的 UTF-8<xref:System.Text.Unicode.Utf8?displayProperty=nameWithType>處理(<xref:System.Text.Rune?displayProperty=nameWithType>包括新 類型和 類型)的更大努力的一部分。 該<xref:System.Text.UTF8Encoding>類型得到了改進的錯誤處理機制,以便生成與新引入的類型一致的輸出。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始,當將<xref:System.Text.UTF8Encoding>位元組轉碼 轉給字元時,類根據 Unicode 最佳實務執行字元替換。 所使用的替換機制由[Unicode 標準版本 12.0、第 3.9(PDF) 在](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf)標題為_U_FFFD 替換最大子部分_的標題中描述。

只當輸入位元組序列包含格式錯誤的 UTF-8 資料時,_此行為才_適用。 此外,<xref:System.Text.UTF8Encoding>如果實例已建`throwOnInvalidBytes: true`構 (請參閱 [UTF8 編碼建構函數<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>`UTF8Encoding`文檔](, 實例將繼續引發無效的輸入,而不是執行 U_FFFD 替換。

下面說明瞭此變更對無效的 3 位元組輸入的影響:

|變形的 3 位元組輸入|在 .NET 核心 3.0 之前輸出|輸出以 .NET 核心 3.0 開頭|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(2 個字元輸出)| `[ FFFD FFFD FFFD ]`(3 個字元輸出)|

根據先前連結的 Unicode 標準 PDF_表 3-9,_ 此 3 字元輸出是首選輸出。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

開發人員不需要執行任何操作。

#### <a name="category"></a>類別

核心 .NET 函式庫

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
