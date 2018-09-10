---
title: 如何：取得離儲存區的存放區
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e2f87bfe1e3e7f3a1c8135c047b25a998793453
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084066"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>如何：取得離儲存區的存放區
隔離存放區會公開資料區間內的虛擬檔案系統。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別提供多種與隔離存放區互動的方法。 若要建立和擷取存放區，<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 提供三種靜態方法：  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> 會傳回使用者和組件所隔離的儲存區。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 會傳回網域和組件所隔離的儲存區。  
  
     這兩種方法都會擷取屬於從中呼叫程式碼的存放區。  
  
-   靜態方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 會傳回透過傳入範圍參數組合所指定的隔離存放區。  
  
 下列程式碼會傳回使用者、組件及網域隔離的存放區。  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法指定存放區應該使用漫遊使用者設定檔漫遊。 如需有關如何設定此功能的詳細資訊，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。  
  
 取自不同組件內的隔離存放區預設是不同的存放區。 您可以在 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法的參數中傳入組件或網域辨識項，藉此存取不同組件或網域的存放區。 這需要依應用程式網域身分識別存取隔離儲存區的權限。 如需詳細資訊，請參閱 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法多載。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法會傳回 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件。 若要協助您決定最適合您情況的隔離類型，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。 當您擁有隔離儲存區檔案物件時，可以使用隔離儲存區方法讀取、寫入、建立以及刪除檔案和目錄。  
  
 沒有任何機制可防止程式碼將 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件傳遞至沒有足夠存取權可取得存放區本身的程式碼。 只有在取得 <xref:System.IO.IsolatedStorage.IsolatedStorage> 物件的參考 (通常是在 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 或 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法中) 時，才會檢查網域和組件的身分識別和隔離儲存區權限。 因此，保護 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件的參考是使用這些參考之程式碼的責任。  
  
## <a name="example"></a>範例  
 下列程式碼可針對取得使用者和組件所隔離之存放區的類別，提供簡單的範例。 您可以變更程式碼，以便透過將 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> 新增至 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法所傳遞的引數，擷取使用者、網域和組件隔離的存放區。  
  
 執行程式碼之後，您可以確認已透過在命令列中輸入 **StoreAdm /LIST** 來建立存放區。 如此會執行[隔離儲存區工具 (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ，並列出目前使用者的所有隔離存放區。  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
- [隔離儲存區](../../../docs/standard/io/isolated-storage.md)  
- [隔離的類型](../../../docs/standard/io/types-of-isolation.md)  
- [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
