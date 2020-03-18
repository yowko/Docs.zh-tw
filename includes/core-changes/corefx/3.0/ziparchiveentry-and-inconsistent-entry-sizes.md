---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568182"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry 不再處理條目大小不一致的存檔

Zip 存檔在中央目錄和本地標頭中列出了壓縮大小和未壓縮大小。  條目資料本身也指示其大小。  在 .NET Core 2.2 和早期版本中，從未檢查過這些值的一致性。 從 .NET 核心 3.0 開始，它們現在就是.

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2<xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>和早期版本中，即使本地標頭與 ZIP 檔案的中央標頭不同，也會成功。 資料將解壓縮，直到達到壓縮流的末尾，即使資料的長度超過中央目錄/本地標頭中列出的未壓縮檔案大小。

從 .NET Core 3.0<xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>開始，該方法檢查本地標頭和中央標頭同意條目的壓縮和未壓縮大小。  否則，如果存檔的本地標頭和/<xref:System.IO.InvalidDataException>或資料描述項清單大小與 ZIP 檔案的中央目錄不同，則該方法將引發 。 讀取條目時，解壓縮資料將被截斷到標頭中列出的未壓縮檔案大小。

進行此更改是為了確保正確<xref:System.IO.Compression.ZipArchiveEntry>表示其資料的大小，並且僅讀取該資料量。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

重新封包出現這些問題的任何 zip 存檔。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
