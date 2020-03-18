---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568195"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3.0 在替換格式錯誤的 UTF-8 位元組序列時遵循 Unicode 最佳實踐

當類<xref:System.Text.UTF8Encoding>在位元組到字元轉碼操作期間遇到格式錯誤的 UTF-8 位元組序列時，它將在輸出字串中用''（U+FFFD 替換字元）替換該序列。 .NET Core 3.0 不同于早期版本的 .NET Core 和 .NET Framework，在轉碼操作期間遵循 Unicode 最佳做法執行此替換。

這是改進整個 .NET 的 UTF-8 處理（包括新<xref:System.Text.Unicode.Utf8?displayProperty=nameWithType>類型和<xref:System.Text.Rune?displayProperty=nameWithType>類型）的更大努力的一部分。 該<xref:System.Text.UTF8Encoding>類型得到了改進的錯誤處理機制，以便生成與新引入的類型一致的輸出。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始，當將位元組轉碼<xref:System.Text.UTF8Encoding>轉給字元時，類根據 Unicode 最佳實踐執行字元替換。 所使用的替換機制由[Unicode 標準版本 12.0、第 3.9（PDF） 在](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf)標題為_U_FFFD 替換最大子部分_的標題中描述。

僅當輸入位元組序列包含格式錯誤的 UTF-8 資料時，_此行為才_適用。 此外，<xref:System.Text.UTF8Encoding>如果實例已構造`throwOnInvalidBytes: true`（請參閱 [UTF8編碼建構函式文檔]（，<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>`UTF8Encoding`實例將繼續引發不正確輸入，而不是執行 U_FFFD 替換。

下面說明了此更改對不正確 3 位元組輸入的影響：

|變形的 3 位元組輸入|在 .NET 核心 3.0 之前輸出|輸出以 .NET 核心 3.0 開頭|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`（2 個字元輸出）| `[ FFFD FFFD FFFD ]`（3 個字元輸出）|

根據先前連結的 Unicode 標準 PDF_表 3-9，_ 此 3 字元輸出是首選輸出。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

開發人員不需要執行任何操作。

#### <a name="category"></a>類別

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
