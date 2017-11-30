---
title: "如何：壓縮與解壓縮檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a>如何：壓縮與解壓縮檔案
<xref:System.IO.Compression>命名空間包含下列型別來壓縮和解壓縮檔案和資料流。 您也可以使用這些類型，以讀取和修改壓縮檔案的內容：  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 下列範例顯示一些使用壓縮的檔案時，您可以執行的函式。  
  
## <a name="example"></a>範例  
 這個範例示範如何建立和解壓縮檔案使用具有.zip 副檔名<xref:System.IO.Compression.ZipFile>類別。 它壓縮資料夾的內容至新的.zip 檔案，然後會擷取該內容發佈至新的資料夾。 若要使用<xref:System.IO.Compression.ZipFile>類別，您必須參考`System.IO.Compression.FileSystem`專案中的組件。  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>範例  
 下一個範例示範如何逐一查看現有的.zip 檔案的內容，將副檔名為.txt 的檔案解壓縮。 它會使用<xref:System.IO.Compression.ZipArchive>類別來存取現有的.zip 檔案，而<xref:System.IO.Compression.ZipArchiveEntry>類別來檢查壓縮檔案中的個別項目。 它會使用擴充方法 (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) 的<xref:System.IO.Compression.ZipArchiveEntry>物件。 擴充方法位於<xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>類別。 若要使用<xref:System.IO.Compression.ZipFileExtensions>類別，您必須參考`System.IO.Compression.FileSystem`專案中的組件。  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>範例  
 下一個範例會使用<xref:System.IO.Compression.ZipArchive>類別來存取現有的.zip 檔案，並將新檔案加入至壓縮的檔案。 當您將它加入至現有的.zip 檔案，取得壓縮的新檔案。  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>範例  
 您也可以使用<xref:System.IO.Compression.GZipStream>和<xref:System.IO.Compression.DeflateStream>來壓縮和解壓縮資料的類別。 它們使用相同的壓縮演算法。 壓縮<xref:System.IO.Compression.GZipStream>物件寫入至副檔名為.gz 檔案可以使用許多常用的工具，除了所提供的方法解壓縮<xref:System.IO.Compression.GZipStream>。 這個範例示範如何壓縮和解壓縮檔案目錄使用<xref:System.IO.Compression.GZipStream>類別。  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [檔案和資料流 I-O](../../../docs/standard/io/index.md)
