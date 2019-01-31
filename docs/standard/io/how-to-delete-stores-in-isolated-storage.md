---
title: HOW TO：刪除隔離儲存區中的存放區
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19a671cac609e79088956ecb4324ebb0a25fb941
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547394"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>HOW TO：刪除隔離儲存區中的存放區
<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別提供兩種方法來刪除隔離儲存區檔案：  
  
-   執行個體方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> 不接受任何引數，並刪除呼叫它的存放區。 這個作業不需要使用權限。 能夠存取存放區的任何程式碼，都可以刪除在它之內的任何或所有資料。  
  
-   靜態方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> 會接受 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 列舉值，並刪除執行程式碼之使用者的所有存放區。 這項作業需要 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 值的 <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> 權限。  
  
## <a name="example"></a>範例  
 下列程式碼範例將示範靜態及執行個體 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> 方法的使用方式。 該類別取得兩個存放區，一個為使用者和組件所隔離，而另一個為使用者、定義域和組件所隔離。 接著呼叫隔離儲存區檔案 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> 的  `isoStore1`方法，刪除使用者、定義域和組件存放區。 然後，使用者所有剩下的存放區是以呼叫靜態方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>的方式刪除。  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
