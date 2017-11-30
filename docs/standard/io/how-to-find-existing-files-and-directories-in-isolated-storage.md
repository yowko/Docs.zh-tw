---
title: "如何：尋找隔離儲存區中的現有檔案和目錄"
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 656c390358b6f6a671cf3ef11ea7be75f897d21c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>如何：尋找隔離儲存區中的現有檔案和目錄
若要搜尋的目錄，隔離儲存區中，使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>方法。 這個方法會採用表示搜尋模式的字串。 您可以使用單一字元 （？） 和多重字元 （*） 萬用字元搜尋模式中，但的萬用字元必須出現在名稱的最後一個部分。 例如，`directory1/*ect*`是有效的搜尋字串，但`*ect*/directory2`不是。  
  
 若要搜尋的檔案，請使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>方法。 在適用於的搜尋字串中使用萬用字元限制<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>也適用於<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>。  
  
 這些方法都不是遞迴。<xref:System.IO.IsolatedStorage.IsolatedStorageFile>類別並不提供任何方法，以列出所有的目錄或存放區中的檔案。 不過，會顯示遞迴方法，在下列程式碼範例。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。 首先，為使用者、 定義域和組件所隔離的存放區會擷取並放置於`isoStore`變數。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A>方法用來設定幾個不同的目錄，而<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29>建構函式會建立這些目錄中的某些檔案。 此程式碼再迴圈的結果`GetAllDirectories`方法。 這個方法會使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>來尋找目前的目錄中的所有目錄名稱。 這些名稱會儲存在陣列中，然後`GetAllDirectories`呼叫其本身，傳遞它發現每個目錄中。 如此一來，所有目錄名稱會都傳回陣列中。 接下來，程式碼會呼叫`GetAllFiles`方法。 這個方法會呼叫`GetAllDirectories`找出所有名稱的目錄，然後檢查每個檔案的目錄使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>方法。 結果會顯示陣列中傳回。  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
