---
title: "如何：列舉目錄和檔案 | Microsoft Docs"
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
  - "I/O [.NET Framework]，列舉目錄和檔案"
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: 18
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：列舉目錄和檔案
您就可以使用傳回目錄和檔案名稱字串之可列舉集合的方法來列舉目錄和檔案。  您也可以使用傳回 <xref:System.IO.DirectoryInfo>、<xref:System.IO.FileInfo> 或 <xref:System.IO.FileSystemInfo> 物件之可列舉集合的方法。  當您使用目錄和檔案的大型集合時，可列舉集合會比陣列提供更好的效能。  
  
 您也可以使用透過這些方法取得的可列舉集合，針對 <xref:System.Collections.Generic.List%601> 類別等集合類別的建構函式提供 <xref:System.Collections.Generic.IEnumerable%601> 參數。  
  
 如果您只想要取得目錄或檔案的名稱，請使用 <xref:System.IO.Directory> 類別的列舉方法。  如果您想要取得目錄或檔案的其他屬性，請使用 <xref:System.IO.DirectoryInfo> 和 <xref:System.IO.FileSystemInfo> 類別。  
  
 下表提供傳回可列舉集合之方法的指南。  
  
|若要列舉|要傳回的可列舉集合|要使用的方法|  
|----------|---------------|------------|  
|目錄|目錄名稱。|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=fullName>|  
||目錄資訊 \(<xref:System.IO.DirectoryInfo>\)。|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=fullName>|  
|檔案|檔案名稱|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=fullName>|  
||檔案資訊 \(<xref:System.IO.FileInfo>\)。|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=fullName>|  
|檔案系統資訊|檔案系統項目。|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=fullName>|  
||檔案系統資訊 \(<xref:System.IO.FileSystemInfo>\)。|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=fullName>|  
  
 雖然您可以使用<xref:System.IO.SearchOption>的 <xref:System.IO.SearchOption> 選項來立即列舉上層目錄之子目錄中的所有檔案，不過未經授權的存取例外狀況 \(<xref:System.UnauthorizedAccessException>\) 可能會導致列舉不完整。  如果這些例外狀況可能會發生，您就可以先列舉目錄，然後再列舉檔案，藉以攔截這些例外狀況。  
  
### 若要列舉目錄名稱  
  
-   請使用 <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=fullName> 方法來取得指定之路徑中最上層目錄名稱的清單。  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### 列舉目錄和子目錄中的檔案名稱。  
  
-   使用 <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=fullName> 方法搜尋目錄和 \(選擇性的\) 其子目錄和取得符合指定之搜尋模式的檔案名稱清單。  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### 若要列舉 DirectoryInfo 物件的集合  
  
-   請使用 <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=fullName> 方法來取得最上層目錄的集合。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### 若要列舉所有目錄中 FileInfo 物件的集合  
  
-   請使用 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=fullName> 方法來取得所有目錄中符合指定之搜尋模式的檔案集合。  這個範例會先列舉最上層目錄，以便攔截可能的未經授權存取例外狀況，然後再列舉檔案。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## 請參閱  
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)