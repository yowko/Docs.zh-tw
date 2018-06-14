---
title: 如何：列舉目錄和檔案
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd7b7542e5cf9352e965717368399dcf4a9ecd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575846"
---
# <a name="how-to-enumerate-directories-and-files"></a>如何：列舉目錄和檔案
您可以使用能夠傳回可列舉其名稱字串集合的方法來列舉目錄和檔案。 您也可以使用傳回可列舉 <xref:System.IO.DirectoryInfo>、<xref:System.IO.FileInfo> 或 <xref:System.IO.FileSystemInfo> 物件集合的方法。 當您使用目錄和檔案的大型集合時，相較於陣列，可列舉的集合會提供更佳的效能。  
  
 您也可以使用取自這些方法的可列舉集合，為集合類別的建構函式提供 <xref:System.Collections.Generic.IEnumerable%601> 參數，例如 <xref:System.Collections.Generic.List%601> 類別。  
  
 如果您想要只取得目錄或檔案的名稱，請使用 <xref:System.IO.Directory> 類別的列舉方法。 如果您想要取得目錄或檔案的其他屬性，請使用 <xref:System.IO.DirectoryInfo> 和 <xref:System.IO.FileSystemInfo> 類別。  
  
 下表將針對傳回可列舉集合的方法，提供指南。  
  
|列舉|要傳回的可列舉集合|要使用的方法|  
|------------------|-------------------------------------|-------------------|  
|目錄|目錄名稱|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||虛擬資訊 (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|檔案|檔案名稱|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||檔案資訊 (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|檔案系統資訊|檔案系統項目|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||檔案系統資訊 (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 雖然您可以使用 <xref:System.IO.SearchOption> 列舉提供的 <xref:System.IO.SearchOption.AllDirectories> 搜尋選項立即列舉父目錄之子目錄中的所有檔案，但是未經授權的存取例外狀況 (<xref:System.UnauthorizedAccessException>) 可能會導致列舉不完整。 如果可能有這些例外狀況，您可以先列舉目錄再列舉檔案來攔截這些例外狀況，然後再繼續。  
  
### <a name="to-enumerate-directory-names"></a>若要列舉目錄名稱  
  
-   使用 <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> 方法，在指定的路徑中取得最上層目錄名稱的清單。  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>若要列舉目錄和子目錄中的檔案名稱  
  
-   使用 <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> 方法搜尋目錄及 (選擇性) 其子目錄，並取得符合指定之搜尋模式的檔案名稱清單。  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>若要列舉 DirectoryInfo 物件的集合  
  
-   使用 <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> 方法取得最上層目錄的集合。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>若要列舉所有目錄中 FileInfo 物件的集合  
  
-   使用 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> 方法，取得符合所有目錄中指定之搜尋模式的檔案集合。 此範例會先列舉最上層目錄來攔截可能未經授權的存取例外狀況，然後再列舉檔案。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [檔案和資料流 I/O](../../../docs/standard/io/index.md)
