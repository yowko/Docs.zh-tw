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
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>如何：列舉隔離儲存區的存放區
您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> 靜態方法，列舉目前使用者的所有隔離存放區。 這個方法會使用 <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 值並傳回 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 列舉值。 若要列舉存放區，您必須擁有<xref:System.Security.Permissions.IsolatedStorageFilePermission>指定的權限<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>值。 如果您呼叫<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>方法<xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>值，它會傳回的陣列<xref:System.IO.IsolatedStorage.IsolatedStorageFile>定義給目前使用者的物件。  
  
## <a name="example"></a>範例  
 下列程式碼範例會取得存放區，以隔離的使用者和組件、 建立一些檔案，並擷取這些檔案使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>方法。  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
