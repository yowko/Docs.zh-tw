---
title: HOW TO：取得隔離儲存區的存放區
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
ms.openlocfilehash: 0968443af28e2d403b08a1af50846e7a1369db49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524568"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="d64b6-102">HOW TO：取得隔離儲存區的存放區</span><span class="sxs-lookup"><span data-stu-id="d64b6-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="d64b6-103">隔離存放區會公開資料區間內的虛擬檔案系統。</span><span class="sxs-lookup"><span data-stu-id="d64b6-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="d64b6-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別提供多種與隔離存放區互動的方法。</span><span class="sxs-lookup"><span data-stu-id="d64b6-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="d64b6-105">若要建立和擷取存放區，<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 提供三種靜態方法：</span><span class="sxs-lookup"><span data-stu-id="d64b6-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
-   <span data-ttu-id="d64b6-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> 會傳回使用者和組件所隔離的儲存區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
-   <span data-ttu-id="d64b6-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 會傳回網域和組件所隔離的儲存區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="d64b6-108">這兩種方法都會擷取屬於從中呼叫程式碼的存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
-   <span data-ttu-id="d64b6-109">靜態方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 會傳回透過傳入範圍參數組合所指定的隔離存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="d64b6-110">下列程式碼會傳回使用者、組件及網域隔離的存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="d64b6-111">您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法指定存放區應該使用漫遊使用者設定檔漫遊。</span><span class="sxs-lookup"><span data-stu-id="d64b6-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="d64b6-112">如需有關如何設定此功能的詳細資訊，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。</span><span class="sxs-lookup"><span data-stu-id="d64b6-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="d64b6-113">取自不同組件內的隔離存放區預設是不同的存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="d64b6-114">您可以在 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法的參數中傳入組件或網域辨識項，藉此存取不同組件或網域的存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="d64b6-115">這需要依應用程式網域身分識別存取隔離儲存區的權限。</span><span class="sxs-lookup"><span data-stu-id="d64b6-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="d64b6-116">如需詳細資訊，請參閱 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法多載。</span><span class="sxs-lookup"><span data-stu-id="d64b6-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="d64b6-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法會傳回 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件。</span><span class="sxs-lookup"><span data-stu-id="d64b6-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="d64b6-118">若要協助您決定最適合您情況的隔離類型，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。</span><span class="sxs-lookup"><span data-stu-id="d64b6-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="d64b6-119">當您擁有隔離儲存區檔案物件時，可以使用隔離儲存區方法讀取、寫入、建立以及刪除檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="d64b6-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="d64b6-120">沒有任何機制可防止程式碼將 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件傳遞至沒有足夠存取權可取得存放區本身的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d64b6-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="d64b6-121">只有在取得 <xref:System.IO.IsolatedStorage.IsolatedStorage> 物件的參考 (通常是在 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 或 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法中) 時，才會檢查網域和組件的身分識別和隔離儲存區權限。</span><span class="sxs-lookup"><span data-stu-id="d64b6-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="d64b6-122">因此，保護 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件的參考是使用這些參考之程式碼的責任。</span><span class="sxs-lookup"><span data-stu-id="d64b6-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d64b6-123">範例</span><span class="sxs-lookup"><span data-stu-id="d64b6-123">Example</span></span>  
 <span data-ttu-id="d64b6-124">下列程式碼可針對取得使用者和組件所隔離之存放區的類別，提供簡單的範例。</span><span class="sxs-lookup"><span data-stu-id="d64b6-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="d64b6-125">您可以變更程式碼，以便透過將 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> 新增至 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法所傳遞的引數，擷取使用者、網域和組件隔離的存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="d64b6-126">執行程式碼之後，您可以確認已透過在命令列中輸入 **StoreAdm /LIST** 來建立存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="d64b6-127">如此會執行[隔離儲存區工具 (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ，並列出目前使用者的所有隔離存放區。</span><span class="sxs-lookup"><span data-stu-id="d64b6-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d64b6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d64b6-128">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="d64b6-129">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="d64b6-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="d64b6-130">隔離的類型</span><span class="sxs-lookup"><span data-stu-id="d64b6-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)
- [<span data-ttu-id="d64b6-131">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="d64b6-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
