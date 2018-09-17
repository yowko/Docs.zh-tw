---
title: 操作說明：壓縮與解壓縮檔案
ms.date: 06/06/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 669936d15cfe1ea125ed36ffdfcfd093b6aacbe1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687630"
---
# <a name="how-to-compress-and-extract-files"></a>操作說明：壓縮與解壓縮檔案

<xref:System.IO.Compression> 命名空間包含壓縮及解壓縮檔案和資料流的下列類型。 您也可以使用這些類型讀取和修改壓縮檔案的內容：

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

下列範例示範您可以在使用壓縮檔案時執行的部分函式。

## <a name="example-1---create-and-extract-a-zip-file"></a>範例 1：建立和解壓縮 .zip 檔案

以下範例示範如何使用 <xref:System.IO.Compression.ZipFile> 類別，建立和解壓縮副檔名為 .zip 的檔案。 它會資料夾的內容壓縮至新的 .zip 檔案，然後將該內容解壓縮至新的資料夾。 若要使用 <xref:System.IO.Compression.ZipFile> 類別，您必須參考專案中的 `System.IO.Compression.FileSystem` 組件。

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a>範例 2：解壓縮特定的檔案副檔名

下一個範例示範如何逐一查看現有 .zip 檔案的內容，並將副檔名為 .txt 的檔案解壓縮。 它會使用 <xref:System.IO.Compression.ZipArchive> 類別存取現有的 .zip 檔案，並使用 <xref:System.IO.Compression.ZipArchiveEntry> 類別檢查壓縮檔案中的個別項目。 它會為 <xref:System.IO.Compression.ZipArchiveEntry> 物件使用擴充方法 (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>)。 擴充方法可在 <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> 類別中使用。 若要使用 <xref:System.IO.Compression.ZipFileExtensions> 類別，您必須參考專案中的 `System.IO.Compression.FileSystem` 組件。

> [!IMPORTANT]
> 當您在解壓縮檔案時，必須尋找惡意的檔案路徑，以免它逸出您要解壓縮的目的目錄。 這是所謂的路徑周遊攻擊。

以下範例示範如何檢查惡意的檔案路徑，並提供安全的方式來解壓縮：

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a>範例 3：將新檔案加入至現有的 .zip 檔案

以下範例使用 <xref:System.IO.Compression.ZipArchive> 類別存取現有的 .zip 檔案，並將新檔案加入至壓縮檔案。 當您將新檔案加入至現有的 .zip 檔案時，會壓縮該檔案。

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a>範例 4：壓縮和解壓縮 .gz 檔案目錄

您也可以使用 <xref:System.IO.Compression.GZipStream> 和 <xref:System.IO.Compression.DeflateStream> 類別壓縮和解壓縮資料。 它們會使用相同的壓縮演算法。 除了 <xref:System.IO.Compression.GZipStream> 所提供的方法之外，寫入至副檔名為 .gz 之檔案的壓縮 <xref:System.IO.Compression.GZipStream> 物件還可以使用許多常用工具解壓縮。 以下範例示範如何使用 <xref:System.IO.Compression.GZipStream> 類別壓縮和解壓縮檔案目錄：

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>另請參閱

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)
