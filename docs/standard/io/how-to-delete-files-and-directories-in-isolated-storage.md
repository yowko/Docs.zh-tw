---
title: "如何：刪除隔離儲存區中的檔案和目錄"
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>如何：刪除隔離儲存區中的檔案和目錄
您可以刪除目錄和檔案中的隔離儲存區檔案。 存放區內，檔案和目錄名稱會是作業系統相依性，且指定相對於根目錄的虛擬檔案系統。 它們是不區分大小寫，在 Windows 作業系統上。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>類別提供兩個方法來刪除目錄和檔案：<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>和<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>。 <xref:System.IO.IsolatedStorage.IsolatedStorageException>如果您嘗試刪除檔案或目錄不存在，會擲回例外狀況。 如果您在名稱中包含萬用字元<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>會擲回<xref:System.IO.IsolatedStorage.IsolatedStorageException>例外狀況，以及<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>會擲回<xref:System.ArgumentException>例外狀況。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>方法失敗時，如果目錄中包含任何檔案或子目錄。 您可以使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>和<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>方法來擷取現有的檔案和目錄。 如需搜尋虛擬檔案系統中的存放區的詳細資訊，請參閱[How to： 隔離儲存區中尋找現有的檔案和目錄](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會建立，，然後刪除 數個目錄和檔案。  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
