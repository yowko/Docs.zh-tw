---
title: 如何：尋找隔離儲存區中的現有檔案和目錄
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c112374458b70a464291e898e9a880c8679773
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44197808"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>如何：尋找隔離儲存區中的現有檔案和目錄
若要搜尋隔離儲存區中的目錄，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> 方法。 此方法會採用表示搜尋模式的字串。 您可以在搜尋模式中使用單一字元 (?) 和多重字元 (*) 萬用字元，但萬用字元必須出現在名稱的最後一個部分。 例如，`directory1/*ect*` 是有效的搜尋字串，但 `*ect*/directory2` 不是。  
  
 若要搜尋檔案，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> 方法。 在搜尋字串中，適用於 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> 的萬用字元限制也適用於 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>。  
  
 這些都不是遞迴方法。<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別不會提供任何方法來列出存放區中的所有目錄或檔案。 不過，遞迴方法會顯示在下列程式碼範例中。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。 首先，系統會擷取針對使用者、網域和組件所隔離的存放區，並放置在 `isoStore` 變數中。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> 方法用來設定幾個不同的目錄，而 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> 建構函式會在這些目錄中建立一些檔案。 接著，此程式碼會在 `GetAllDirectories` 方法的結果中執行迴圈。 此方法會使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> 尋找目前目錄中的所有目錄名稱。 這些名稱會儲存在陣列中，然後 `GetAllDirectories` 會呼叫其本身，進而傳入所找到的每個目錄。 因此，陣列中會傳回所有目錄名稱。 接下來，此程式碼會呼叫 `GetAllFiles` 方法。 此方法會呼叫 `GetAllDirectories` 來找出所有目錄的名稱，然後使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> 方法檢查每個目錄中的檔案。 陣列中會傳回結果以供顯示。  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
