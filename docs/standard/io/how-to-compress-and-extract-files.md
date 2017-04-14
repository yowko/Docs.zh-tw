---
title: "如何：壓縮與解壓縮檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "I/O [.NET Framework]，壓縮"
  - "壓縮"
  - "壓縮檔案"
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: 19
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：壓縮與解壓縮檔案
<xref:System.IO.Compression> 命名空間包含壓縮及解壓縮的檔案和資料流如下列型別。  您也可以使用這些型別讀取和修改壓縮檔案的內容:  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 下列範例示範您可以執行工作，與壓縮檔時的某些函式。  
  
## 範例  
 這個範例顯示如何建立和擷取使用 <xref:System.IO.Compression.ZipFile> 類別，具有副檔名 .zip 檔的壓縮檔。  壓縮資料夾的內容到新的 .zip 檔，然後擷取內容到新資料夾。  若要使用 <xref:System.IO.Compression.ZipFile> 類別，您必須參考您專案的 `System.IO.Compression.FileSystem` 組件。  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## 範例  
 下一個範例顯示如何從現有的 .zip 檔擷取 .txt 副檔名的檔案。  它會使用 <xref:System.IO.Compression.ZipArchive> 類別存取現有的 .zip 檔案和 <xref:System.IO.Compression.ZipArchiveEntry> 類別檢查封裝成壓縮檔中的個別項目。  它會使用 <xref:System.IO.Compression.ZipArchiveEntry> 物件擴充方法 \(<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>\)。  擴充方法在 <xref:System.IO.Compression.ZipFileExtensions?displayProperty=fullName> 類別。  若要使用 <xref:System.IO.Compression.ZipFileExtensions> 類別，您必須參考您專案的 `System.IO.Compression.FileSystem` 組件。  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## 範例  
 下一個範例使用 <xref:System.IO.Compression.ZipArchive> 類別存取現有的 .zip 檔案，然後將新檔案加入至壓縮檔。  將它加入至現有的 .zip 檔案時，新的檔案會壓縮。  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## 範例  
 您也可以使用 <xref:System.IO.Compression.GZipStream> 和 <xref:System.IO.Compression.DeflateStream> 類別壓縮及解壓縮資料。  它們使用相同的壓縮演算法。  寫入檔案副檔名為 .gz 的壓縮 <xref:System.IO.Compression.GZipStream> 物件可以使用許多泛型工具解壓縮。 <xref:System.IO.Compression.GZipStream>提供的方法。  本範例顯示如何使用 <xref:System.IO.Compression.GZipStream> 類別來壓縮和解壓縮檔案的目錄。  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## 請參閱  
 <xref:System.IO.Compression.ZipArchive>   
 <xref:System.IO.Compression.ZipFile>   
 <xref:System.IO.Compression.ZipArchiveEntry>   
 <xref:System.IO.Compression.DeflateStream>   
 <xref:System.IO.Compression.GZipStream>   
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)