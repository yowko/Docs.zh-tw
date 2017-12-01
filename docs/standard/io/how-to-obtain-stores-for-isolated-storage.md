---
title: "如何：取得離儲存區的存放區"
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
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb0b877aa0f4cee36bd1f8c1cea624cf9368fbaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>如何：取得離儲存區的存放區
隔離儲存區會公開資料區間內的虛擬檔案系統。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>類別提供多個與隔離存放區互動的方法。 若要建立和擷取的存放區<xref:System.IO.IsolatedStorage.IsolatedStorageFile>提供三種靜態方法：  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>傳回使用者和組件所隔離的存放裝置。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>傳回儲存體隔離之定義域和組件。  
  
     這兩種方法會擷取屬於從中呼叫它們的程式碼的存放區。  
  
-   靜態方法<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>傳回所指定範圍參數的組合，傳遞隔離存放區。  
  
 下列程式碼會傳回依使用者、 組件及網域隔離的存放區。  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 您可以使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法，以指定存放區應漫遊與漫遊使用者設定檔。 如需有關如何設定此功能的詳細資訊，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。  
  
 是取自內不同的組件的隔離存放區根據預設，在不同存放區。 您可以藉由傳遞存取不同的組件或網域存放區中的組件或定義域的辨識項參數中<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法。 這需要應用程式定義域識別來存取隔離儲存區的權限。 如需詳細資訊，請參閱<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法多載。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>， <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>，和<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法會傳回<xref:System.IO.IsolatedStorage.IsolatedStorageFile>物件。 若要協助您決定最適合您情況的隔離類型，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。 當您擁有隔離儲存區檔案 」 物件時，您可以使用隔離儲存區方法來讀取、 寫入、 建立及刪除檔案和目錄。  
  
 沒有傳遞可防止程式碼沒有機制<xref:System.IO.IsolatedStorage.IsolatedStorageFile>物件，該程式碼並沒有足夠的存取權，以取得存放區本身。 參考時才會檢查定義域和組件的識別和隔離儲存區使用權限<xref:System.IO.IsolatedStorage.IsolatedStorage>取得的物件，通常在<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>， <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>，或<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法。 保護參考<xref:System.IO.IsolatedStorage.IsolatedStorageFile>物件負責，因此，使用這些參考的程式碼。  
  
## <a name="example"></a>範例  
 下列程式碼提供簡單的範例，取得使用者和組件所隔離的存放區的類別。 可以變更的程式碼，以擷取藉由新增使用者、 定義域和組件所隔離的存放區<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType>的引數，<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法傳遞。  
  
 您執行程式碼之後，您可以確認已輸入中建立的存放區**StoreAdm /LIST**在命令列。 這會執行[隔離儲存區工具 (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ，並列出所有目前的隔離儲存的使用者。  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)  
 [隔離的類型](../../../docs/standard/io/types-of-isolation.md)  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
