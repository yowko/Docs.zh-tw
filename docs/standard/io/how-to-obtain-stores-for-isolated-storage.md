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
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="3e39f-102">如何：取得離儲存區的存放區</span><span class="sxs-lookup"><span data-stu-id="3e39f-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="3e39f-103">隔離儲存區會公開資料區間內的虛擬檔案系統。</span><span class="sxs-lookup"><span data-stu-id="3e39f-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="3e39f-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>類別提供多個與隔離存放區互動的方法。</span><span class="sxs-lookup"><span data-stu-id="3e39f-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="3e39f-105">若要建立和擷取的存放區<xref:System.IO.IsolatedStorage.IsolatedStorageFile>提供三種靜態方法：</span><span class="sxs-lookup"><span data-stu-id="3e39f-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
-   <span data-ttu-id="3e39f-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>傳回使用者和組件所隔離的存放裝置。</span><span class="sxs-lookup"><span data-stu-id="3e39f-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
-   <span data-ttu-id="3e39f-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>傳回儲存體隔離之定義域和組件。</span><span class="sxs-lookup"><span data-stu-id="3e39f-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="3e39f-108">這兩種方法會擷取屬於從中呼叫它們的程式碼的存放區。</span><span class="sxs-lookup"><span data-stu-id="3e39f-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
-   <span data-ttu-id="3e39f-109">靜態方法<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>傳回所指定範圍參數的組合，傳遞隔離存放區。</span><span class="sxs-lookup"><span data-stu-id="3e39f-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="3e39f-110">下列程式碼會傳回依使用者、 組件及網域隔離的存放區。</span><span class="sxs-lookup"><span data-stu-id="3e39f-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="3e39f-111">您可以使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法，以指定存放區應漫遊與漫遊使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="3e39f-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="3e39f-112">如需有關如何設定此功能的詳細資訊，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。</span><span class="sxs-lookup"><span data-stu-id="3e39f-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="3e39f-113">是取自內不同的組件的隔離存放區根據預設，在不同存放區。</span><span class="sxs-lookup"><span data-stu-id="3e39f-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="3e39f-114">您可以藉由傳遞存取不同的組件或網域存放區中的組件或定義域的辨識項參數中<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3e39f-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="3e39f-115">這需要應用程式定義域識別來存取隔離儲存區的權限。</span><span class="sxs-lookup"><span data-stu-id="3e39f-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="3e39f-116">如需詳細資訊，請參閱<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法多載。</span><span class="sxs-lookup"><span data-stu-id="3e39f-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="3e39f-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>， <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>，和<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法會傳回<xref:System.IO.IsolatedStorage.IsolatedStorageFile>物件。</span><span class="sxs-lookup"><span data-stu-id="3e39f-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="3e39f-118">若要協助您決定最適合您情況的隔離類型，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。</span><span class="sxs-lookup"><span data-stu-id="3e39f-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="3e39f-119">當您擁有隔離儲存區檔案 」 物件時，您可以使用隔離儲存區方法來讀取、 寫入、 建立及刪除檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="3e39f-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="3e39f-120">沒有傳遞可防止程式碼沒有機制<xref:System.IO.IsolatedStorage.IsolatedStorageFile>物件，該程式碼並沒有足夠的存取權，以取得存放區本身。</span><span class="sxs-lookup"><span data-stu-id="3e39f-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="3e39f-121">參考時才會檢查定義域和組件的識別和隔離儲存區使用權限<xref:System.IO.IsolatedStorage.IsolatedStorage>取得的物件，通常在<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>， <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>，或<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3e39f-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="3e39f-122">保護參考<xref:System.IO.IsolatedStorage.IsolatedStorageFile>物件負責，因此，使用這些參考的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3e39f-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e39f-123">範例</span><span class="sxs-lookup"><span data-stu-id="3e39f-123">Example</span></span>  
 <span data-ttu-id="3e39f-124">下列程式碼提供簡單的範例，取得使用者和組件所隔離的存放區的類別。</span><span class="sxs-lookup"><span data-stu-id="3e39f-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="3e39f-125">可以變更的程式碼，以擷取藉由新增使用者、 定義域和組件所隔離的存放區<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType>的引數，<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法傳遞。</span><span class="sxs-lookup"><span data-stu-id="3e39f-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="3e39f-126">您執行程式碼之後，您可以確認已輸入中建立的存放區**StoreAdm /LIST**在命令列。</span><span class="sxs-lookup"><span data-stu-id="3e39f-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="3e39f-127">這會執行[隔離儲存區工具 (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ，並列出所有目前的隔離儲存的使用者。</span><span class="sxs-lookup"><span data-stu-id="3e39f-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="3e39f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e39f-128">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="3e39f-129">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="3e39f-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="3e39f-130">隔離的類型</span><span class="sxs-lookup"><span data-stu-id="3e39f-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)  
 [<span data-ttu-id="3e39f-131">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="3e39f-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
