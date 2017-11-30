---
title: "如何：列舉隔離儲存區的存放區"
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
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f8863f1d8b3c7f4ed8f65f8f8eb3e8af51b0405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="ba1cc-102">如何：列舉隔離儲存區的存放區</span><span class="sxs-lookup"><span data-stu-id="ba1cc-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="ba1cc-103">您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> 靜態方法，列舉目前使用者的所有隔離存放區。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="ba1cc-104">這個方法會使用 <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 值並傳回 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="ba1cc-105">若要列舉存放區，您必須擁有<xref:System.Security.Permissions.IsolatedStorageFilePermission>指定的權限<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>值。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="ba1cc-106">如果您呼叫<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>方法<xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>值，它會傳回的陣列<xref:System.IO.IsolatedStorage.IsolatedStorageFile>定義給目前使用者的物件。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba1cc-107">範例</span><span class="sxs-lookup"><span data-stu-id="ba1cc-107">Example</span></span>  
 <span data-ttu-id="ba1cc-108">下列程式碼範例會取得存放區，以隔離的使用者和組件、 建立一些檔案，並擷取這些檔案使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ba1cc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba1cc-109">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="ba1cc-110">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="ba1cc-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
