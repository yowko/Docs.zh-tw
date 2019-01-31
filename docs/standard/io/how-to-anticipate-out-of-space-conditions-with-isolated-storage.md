---
title: HOW TO：預期隔離儲存區發生空間不足的情況
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be3c38c1cf1e6fa6f2bfd5fed05ee8150309d7d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609677"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="ddb79-102">HOW TO：預期隔離儲存區發生空間不足的情況</span><span class="sxs-lookup"><span data-stu-id="ddb79-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>
<span data-ttu-id="ddb79-103">使用隔離儲存區的程式碼受到[配額](../../../docs/standard/io/isolated-storage.md#quotas)的限制，此限制可針對隔離儲存區檔案和目錄所在的資料區間，指定其大小上限。</span><span class="sxs-lookup"><span data-stu-id="ddb79-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="ddb79-104">配額由安全性原則所定義且由系統管理員設定。</span><span class="sxs-lookup"><span data-stu-id="ddb79-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="ddb79-105">當您嘗試寫入資料時，如果超過允許的大小上限，則會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況，且作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="ddb79-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="ddb79-106">這有助於防止惡意的拒絕服務攻擊，此功能可能會因為資料存放區已滿而導致應用程式拒絕要求。</span><span class="sxs-lookup"><span data-stu-id="ddb79-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>  
  
 <span data-ttu-id="ddb79-107">為協助您判斷指定的寫入嘗試是否可能因為這個原因而失敗，<xref:System.IO.IsolatedStorage.IsolatedStorage> 類別會提供三個唯讀屬性：<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>。</span><span class="sxs-lookup"><span data-stu-id="ddb79-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="ddb79-108">您可以使用這些屬性判斷寫入存放區是否會導致超過存放區允許的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ddb79-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="ddb79-109">請記住，您可以並行存取隔離儲存區。因此，在計算剩餘的儲存區數量時，可能會在您嘗試寫入存放區時耗用儲存空間。</span><span class="sxs-lookup"><span data-stu-id="ddb79-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="ddb79-110">不過，您可以使用存放區的大小上限，以協助判斷是否即將到達可用儲存空間的上限。</span><span class="sxs-lookup"><span data-stu-id="ddb79-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>  
  
 <span data-ttu-id="ddb79-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> 屬性相依於組件的辨識項，才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="ddb79-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="ddb79-112">因此，您僅能針對使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 或 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法建立的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件，擷取此屬性。</span><span class="sxs-lookup"><span data-stu-id="ddb79-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="ddb79-113">以其他任何方式所建立的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件 (例如，從 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> 方法傳回的物件) 將不會傳回精確的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ddb79-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddb79-114">範例</span><span class="sxs-lookup"><span data-stu-id="ddb79-114">Example</span></span>  
 <span data-ttu-id="ddb79-115">下列程式碼範例會取得隔離儲存區、建立一些檔案，然後擷取 <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ddb79-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="ddb79-116">剩餘的空間會以位元組為單位來報告。</span><span class="sxs-lookup"><span data-stu-id="ddb79-116">The remaining space is reported in bytes.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="ddb79-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddb79-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="ddb79-118">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="ddb79-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="ddb79-119">如何：取得隔離儲存區的存放區</span><span class="sxs-lookup"><span data-stu-id="ddb79-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
