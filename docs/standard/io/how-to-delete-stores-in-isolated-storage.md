---
title: 如何：刪除隔離儲存區中的存放區
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
ms.openlocfilehash: cfb6111b080b7c8c359458e3fd1dc99cb0ff3c36
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877316"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="c91c1-102">如何：刪除隔離儲存區中的存放區</span><span class="sxs-lookup"><span data-stu-id="c91c1-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="c91c1-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別提供兩種方法來刪除隔離儲存區檔案：</span><span class="sxs-lookup"><span data-stu-id="c91c1-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="c91c1-104">執行個體方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> 不接受任何引數，並刪除呼叫它的存放區。</span><span class="sxs-lookup"><span data-stu-id="c91c1-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="c91c1-105">這個作業不需要使用權限。</span><span class="sxs-lookup"><span data-stu-id="c91c1-105">No permissions are required for this operation.</span></span> <span data-ttu-id="c91c1-106">能夠存取存放區的任何程式碼，都可以刪除在它之內的任何或所有資料。</span><span class="sxs-lookup"><span data-stu-id="c91c1-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="c91c1-107">靜態方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> 會接受 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 列舉值，並刪除執行程式碼之使用者的所有存放區。</span><span class="sxs-lookup"><span data-stu-id="c91c1-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="c91c1-108">這項作業需要 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 值的 <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> 權限。</span><span class="sxs-lookup"><span data-stu-id="c91c1-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c91c1-109">範例</span><span class="sxs-lookup"><span data-stu-id="c91c1-109">Example</span></span>  
 <span data-ttu-id="c91c1-110">下列程式碼範例將示範靜態及執行個體 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> 方法的使用方式。</span><span class="sxs-lookup"><span data-stu-id="c91c1-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="c91c1-111">該類別取得兩個存放區，一個為使用者和組件所隔離，而另一個為使用者、定義域和組件所隔離。</span><span class="sxs-lookup"><span data-stu-id="c91c1-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="c91c1-112">接著呼叫隔離儲存區檔案 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> 的  `isoStore1`方法，刪除使用者、定義域和組件存放區。</span><span class="sxs-lookup"><span data-stu-id="c91c1-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="c91c1-113">然後，使用者所有剩下的存放區是以呼叫靜態方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>的方式刪除。</span><span class="sxs-lookup"><span data-stu-id="c91c1-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c91c1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c91c1-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [<span data-ttu-id="c91c1-115">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="c91c1-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
