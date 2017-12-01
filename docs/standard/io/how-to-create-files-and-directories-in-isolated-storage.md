---
title: "如何：在隔離儲存區中建立檔案和目錄"
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
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>如何：在隔離儲存區中建立檔案和目錄
取得隔離存放區之後，您可以建立目錄和檔案來儲存資料。 存放區內，檔案和目錄名稱被指定相對於根目錄的虛擬檔案系統。  
  
 若要建立目錄，使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>執行個體方法。 如果您指定不存在目錄的子目錄，則會建立兩個目錄。 如果您指定的目錄已經存在，則方法會傳回而不需要建立一個目錄，並擲回任何例外狀況。 不過，如果您指定的目錄名稱包含無效的字元，<xref:System.IO.IsolatedStorage.IsolatedStorageException>擲回例外狀況。  
  
 若要建立檔案，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> 方法。  
  
 在 Windows 作業系統、 隔離儲存區檔案和目錄名稱不區分大小寫。 也就是說，如果您建立名為`ThisFile.txt`，然後再建立另一個名為的檔案`THISFILE.TXT`，會建立一個檔案。 檔案名稱會保留其原始大小寫用於顯示用途。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
