---
title: 作法：預期隔離儲存區發生空間不足的情況
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf5144cb1abd3a916d2b5afc361c8c96a221d47e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372291"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>作法：預期隔離儲存區發生空間不足的情況

使用隔離儲存區的程式碼受到[配額](../../../docs/standard/io/isolated-storage.md#quotas)的限制，此限制可針對隔離儲存區檔案和目錄所在的資料區間，指定其大小上限。 配額由安全性原則所定義且由系統管理員設定。 當您嘗試寫入資料時，如果超過允許的大小上限，則會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況，且作業會失敗。 這有助於防止惡意的拒絕服務攻擊，此功能可能會因為資料存放區已滿而導致應用程式拒絕要求。

為協助您判斷指定的寫入嘗試是否可能因為這個原因而失敗，<xref:System.IO.IsolatedStorage.IsolatedStorage> 類別會提供三個唯讀屬性：<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>。 您可以使用這些屬性判斷寫入存放區是否會導致超過存放區允許的大小上限。 請記住，您可以並行存取隔離儲存區。因此，在計算剩餘的儲存區數量時，可能會在您嘗試寫入存放區時耗用儲存空間。 不過，您可以使用存放區的大小上限，以協助判斷是否即將到達可用儲存空間的上限。

<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> 屬性相依於組件的辨識項，才能正常運作。 因此，您僅能針對使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 或 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法建立的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件，擷取此屬性。 以其他任何方式所建立的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件 (例如，從 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> 方法傳回的物件) 將不會傳回精確的大小上限。

## <a name="example"></a>範例

下列程式碼範例會取得隔離儲存區、建立一些檔案，然後擷取 <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> 屬性。 剩餘的空間會以位元組為單位來報告。

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>另請參閱

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
- [如何：取得隔離儲存區的存放區](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
