---
title: "如何：列舉目錄和檔案"
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
helpviewer_keywords: I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: caf9bdec017a5466269ff7fe97be4d0243035b4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-directories-and-files"></a>如何：列舉目錄和檔案
您可以藉由傳回字串，其名稱的可列舉集合的方法來列舉目錄和檔案。 您也可以使用傳回的可列舉集合的方法<xref:System.IO.DirectoryInfo>， <xref:System.IO.FileInfo>，或<xref:System.IO.FileSystemInfo>物件。 當您使用的目錄和檔案的大型集合，可列舉集合會提供更佳的效能比陣列。  
  
 您也可以使用這些方法從取得的可列舉集合，提供<xref:System.Collections.Generic.IEnumerable%601>參數集合的建構函式之類的類別<xref:System.Collections.Generic.List%601>類別。  
  
 如果您想要取得目錄或檔案的名稱，使用的列舉型別方法<xref:System.IO.Directory>類別。 如果您想要取得目錄或檔案的其他屬性，使用<xref:System.IO.DirectoryInfo>和<xref:System.IO.FileSystemInfo>類別。  
  
 下表將提供指南，以傳回可列舉集合的方法。  
  
|列舉|要傳回的可列舉集合|若要使用的方法|  
|------------------|-------------------------------------|-------------------|  
|目錄|目錄名稱|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||目錄資訊 (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|檔案|檔案名稱|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||檔案資訊 (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|檔案系統資訊|檔案系統項目|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||檔案系統資訊 (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 雖然您可以使用，以立即列舉父目錄的子目錄中的所有檔案<xref:System.IO.SearchOption.AllDirectories>搜尋所提供的選項<xref:System.IO.SearchOption>列舉型別、 未經授權的存取例外狀況 (<xref:System.UnauthorizedAccessException>) 可能會導致將列舉不完整。 如果可能會有這些例外狀況，您可以攔截，並繼續先列舉目錄和然後列舉檔案。  
  
### <a name="to-enumerate-directory-names"></a>若要列舉的目錄名稱  
  
-   使用<xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType>方法，以取得指定之路徑中的最上層目錄名稱的清單。  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>列舉目錄和子目錄中的檔案名稱  
  
-   使用<xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType>方法來搜尋目錄，以及 （選擇性） 及其子目錄中，以及取得符合指定的搜尋模式的檔案名稱的清單。  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>列舉 DirectoryInfo 物件的集合  
  
-   使用<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>方法，以取得最上層目錄的集合。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>若要列舉所有目錄中的 FileInfo 物件的集合  
  
-   使用<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>方法，以取得符合指定的搜尋模式的所有目錄中檔案的集合。 本範例先列舉攔截可能未經授權的存取例外狀況，最上層的目錄，然後列舉的檔案。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流 I-O](../../../docs/standard/io/index.md)
