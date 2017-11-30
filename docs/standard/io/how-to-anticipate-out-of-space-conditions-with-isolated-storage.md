---
title: "如何：預期隔離儲存區發生空間不足的情況"
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
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d813522d0aeb9bf37582c167760d44268df27039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>如何：預期隔離儲存區發生空間不足的情況
使用隔離儲存區的程式碼由限制[配額](../../../docs/standard/io/isolated-storage.md#quotas)所在的資料區間隔離儲存區檔案和目錄存在指定的最大值。 配額由安全性原則所定義且由系統管理員設定。 如果當您嘗試寫入資料，大小超過允許的最大<xref:System.IO.IsolatedStorage.IsolatedStorageException>擲回例外狀況，則作業會失敗。 這有助於防止惡意的阻絕服務攻擊可能會導致拒絕要求，因為資料存放區會填入應用程式。  
  
 若要可協助您判斷是否可能失敗，因此，在指定的寫入嘗試<xref:System.IO.IsolatedStorage.IsolatedStorage>類別會提供三個唯讀屬性： <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>， <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>，和<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>。 您可以使用這些屬性來判斷是否寫入至存放區會導致超過存放區的大小上限。 請記住，隔離儲存區可以並行; 存取因此，當您計算剩餘的儲存體數量，儲存空間會耗用您嘗試寫入存放區的時間。 不過，您可以使用存放區的大小上限，以協助判斷是否即將到達上限上可用的存放裝置。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>屬性取決於從才能正常運作的組件的辨識項。 基於這個理由，您應該擷取這個屬性只在<xref:System.IO.IsolatedStorage.IsolatedStorageFile>使用所建立的物件<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>， <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>，或<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>任何其他方式所建立的物件 (例如，從傳回的物件<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>方法) 將不會傳回精確的最大大小。  
  
## <a name="example"></a>範例  
 下列程式碼範例會取得隔離儲存區、 建立一些檔案，並擷取<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>屬性。 剩餘的空間會以位元組為單位來報告。  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)  
 [如何：取得隔離儲存區的存放區](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
