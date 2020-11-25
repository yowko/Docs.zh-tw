---
ms.openlocfilehash: 8c8e87c885c99d28aa9a7a5d5a2b48c80d40d7db
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032039"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry 不再以不一致的專案大小處理封存

Zip 封存會列出中央目錄和本機標頭中的壓縮大小和未壓縮大小。  專案資料本身也會指出其大小。  在 .NET Core 2.2 及更早版本中，這些值絕對不會檢查一致性。 從 .NET Core 3.0 開始，它們現在是。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 及更早版本中， <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 即使本機標頭是以 zip 檔案的中央標頭不同意，也會成功。 除非壓縮資料流程結束，否則資料會進行解壓縮，即使其長度超過中央目錄/本機標頭中所列的未壓縮檔案大小。

從 .NET Core 3.0 開始，此 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 方法會檢查本機標頭和中央標頭是否同意專案的壓縮和未壓縮大小。  如果沒有，則方法會在封存 <xref:System.IO.InvalidDataException> 的本機標頭和/或資料描述項清單大小與 zip 檔案的中央目錄不一致時擲回。 讀取專案時，解壓縮的資料會截斷為標頭中所列的未壓縮檔案大小。

進行這項變更是為了確保 <xref:System.IO.Compression.ZipArchiveEntry> 正確表示其資料的大小，以及唯讀取該資料量。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

重新封裝任何展示這些問題的 zip 封存。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
