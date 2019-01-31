---
title: HOW TO：刪除隔離儲存區中的檔案和目錄
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538020"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>HOW TO：刪除隔離儲存區中的檔案和目錄
您可以刪除隔離儲存區檔案中的目錄和檔案。 在存放區內，檔案和目錄名稱都與作業系統相依，且會指定為相對於虛擬檔案系統的根目錄。 它們在 Windows 作業系統上不區分大小寫。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> 類別提供兩種方法來刪目錄和檔案：<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>。 如果您嘗試刪除不存在的檔案或目錄，會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況。 如果您在名稱中包含萬用字元，<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> 會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況，且 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> 會擲回 <xref:System.ArgumentException> 例外狀況。  
  
 如果目錄中包含任何檔案或子目錄，則 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> 方法將會失敗。 您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> 方法擷取現有的檔案和目錄。 如需搜尋存放區之虛擬檔案系統的詳細資訊，請參閱[如何：尋找隔離儲存區中的現有檔案和目錄](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會建立數個目錄和檔案，然後再加以刪除。  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
