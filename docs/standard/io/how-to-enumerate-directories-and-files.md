---
title: HOW TO：列舉目錄和檔案
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c751ab03875b6af89c325981c65b7bc69d0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580456"
---
# <a name="how-to-enumerate-directories-and-files"></a>HOW TO：列舉目錄和檔案
當您使用目錄和檔案的大型集合時，相較於陣列，可列舉的集合會提供更佳的效能。 若要列舉目錄和檔案，請使用能夠傳回可列舉目錄或檔案名稱、或是其 <xref:System.IO.DirectoryInfo>、<xref:System.IO.FileInfo> 或 <xref:System.IO.FileSystemInfo> 物件集合的方法。  
  
如果您想要搜尋並只傳回目錄或檔案的名稱，請使用 <xref:System.IO.Directory> 類別的列舉方法。 如果您想要搜尋並傳回目錄或檔案的其他屬性，請使用 <xref:System.IO.DirectoryInfo> 和 <xref:System.IO.FileSystemInfo> 類別。  
  
您可以使用來自這些方法的可列舉集合，作為 <xref:System.Collections.Generic.List%601> 等集合類別建構函式的 <xref:System.Collections.Generic.IEnumerable%601> 參數。  
  
下表摘要說明能夠傳回可列舉檔案和目錄集合的方法：  
  
|搜尋並傳回|使用方法|  
|------------------|-------------------------------------|-------------------|  
|目錄名稱|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|虛擬資訊 (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|檔案名稱|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|檔案資訊 (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|檔案系統項目名稱|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|檔案系統項目資訊 (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|目錄和檔案名稱 |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> 雖然您可以使用選擇性 <xref:System.IO.SearchOption> 列舉的 <xref:System.IO.SearchOption.AllDirectories> 選項立即列舉父目錄中子目錄的所有檔案，但 <xref:System.UnauthorizedAccessException> 錯誤可能會使列舉不完整。 您可以先列舉目錄再列舉檔案來攔截這些例外狀況。  
  
## <a name="examples-use-the-directory-class"></a>例如：使用 Directory 類別  
  
下列範例使用 <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> 方法，在所指定路徑中取得最上層目錄名稱的清單。  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

下列範例使用 <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> 方法，以遞迴方式列舉目錄和子目錄中符合特定模式的所有檔案名稱。 然後，它會讀取每個檔案的每一行，並顯示包含指定字串的行，以及其檔名和路徑。

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>例如：使用 DirectoryInfo 類別  
  
下列範例使用 <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> 方法，列出其 <xref:System.IO.FileSystemInfo.CreationTimeUtc> 早於特定 <xref:System.DateTime> 值的最上層目錄集合。  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
下列範例使用 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> 方法，列出其 <xref:System.IO.FileInfo.Length> 超過 10 MB 的所有檔案。 此範例會先列舉最上層目錄來攔截可能未經授權的存取例外狀況，再列舉檔案。  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱

[檔案和資料流 I/O](../../../docs/standard/io/index.md)
