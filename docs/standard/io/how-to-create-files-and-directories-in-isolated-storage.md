---
title: 作法：在隔離儲存區中建立檔案和目錄
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET], isolated storage
- files [.NET], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: 75afb19a551174b9386259ebff871d4a54b68f01
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830801"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>作法：在隔離儲存區中建立檔案和目錄

取得隔離儲存區之後，您可以建立目錄和檔案來儲存資料。 在存放區內，系統會以相對於虛擬檔案系統的根目錄指定檔案和目錄名稱。  
  
 若要建立目錄，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> 執行個體方法。 如果您指定不存在之目錄的子目錄，則會建立這兩個目錄。 如果您指定已經存在的目錄，則會傳回方法而不會建立目錄，而且不會擲回任何例外狀況。 不過，如果您指定包含無效字元的目錄名稱，則會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況。  
  
 若要建立檔案，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> 方法。  
  
 在 Windows 作業系統中，隔離儲存區檔案和目錄名稱不區分大小寫。 也就是說，如果您建立名為 `ThisFile.txt` 的檔案，然後再建立名為 `THISFILE.TXT` 的另一個檔案，則只會建立一個檔案。 基於顯示用途，檔案名稱會保留其原始大小寫。  

 <xref:System.IO.IsolatedStorage.IsolatedStorageException>如果路徑包含的目錄不存在，則建立隔離儲存區檔案將會擲回。
  
## <a name="example"></a>範例  
 下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [隔離儲存區](isolated-storage.md)
