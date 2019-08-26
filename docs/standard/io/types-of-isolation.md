---
title: 隔離的類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8875ed10c4cb144995b602287f904d3c98dcdb39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948769"
---
# <a name="types-of-isolation"></a><span data-ttu-id="f1b4c-102">隔離的類型</span><span class="sxs-lookup"><span data-stu-id="f1b4c-102">Types of Isolation</span></span>
<span data-ttu-id="f1b4c-103">對隔離儲存區的存取永遠限制於建立該隔離儲存區的使用者。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-103">Access to isolated storage is always restricted to the user who created it.</span></span> <span data-ttu-id="f1b4c-104">為實作這種類型的隔離，通用語言執行階段會使用作業系統可辨識的相同使用者身分識別概念，這是與開啟儲存區時，與程式碼執行所在處理序相關聯的身分識別。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-104">To implement this type of isolation, the common language runtime uses the same notion of user identity that the operating system recognizes, which is the identity associated with the process in which the code is running when the store is opened.</span></span> <span data-ttu-id="f1b4c-105">此身分識別是一個經過驗證的使用者身分識別，但是模擬可能會造成目前使用者的身分識別動態變更。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-105">This identity is an authenticated user identity, but impersonation can cause the identity of the current user to change dynamically.</span></span>  
  
 <span data-ttu-id="f1b4c-106">對隔離儲存區的存取也會根據與應用程式網域和組件相關聯的身分識別，或單獨與組件相關聯的身分識別而受到限制。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-106">Access to isolated storage is also restricted according to the identity associated with the application's domain and assembly, or with the assembly alone.</span></span> <span data-ttu-id="f1b4c-107">執行階段會以下列方式取得這些身分識別：</span><span class="sxs-lookup"><span data-stu-id="f1b4c-107">The runtime obtains these identities in the following ways:</span></span>  
  
- <span data-ttu-id="f1b4c-108">網域身分識別代表應用程式的辨識項，若是 Web 應用程式，則可能是完整 URL。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-108">Domain identity represents the evidence of the application, which in the case of a web application might be the full URL.</span></span> <span data-ttu-id="f1b4c-109">針對殼層裝載的程式碼，網域身分識別可能會以應用程式目錄路徑為基礎。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-109">For shell-hosted code, the domain identity might be based on the application directory path.</span></span> <span data-ttu-id="f1b4c-110">例如，如果可執行檔從路徑 C:\Office\MyApp.exe 執行，網域身分識別將為 C:\Office\MyApp.exe。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-110">For example, if the executable runs from the path C:\Office\MyApp.exe, the domain identity would be C:\Office\MyApp.exe.</span></span>  
  
- <span data-ttu-id="f1b4c-111">組件身分識別是組件的辨識項。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-111">Assembly identity is the evidence of the assembly.</span></span> <span data-ttu-id="f1b4c-112">這可能是來自密碼編譯數位簽章，它可以是組件的[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)、組件的軟體發行者或其 URL 識別。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-112">This might come from a cryptographic digital signature, which can be the assembly's [strong name](../../../docs/framework/app-domains/strong-named-assemblies.md), the software publisher of the assembly, or its URL identity.</span></span> <span data-ttu-id="f1b4c-113">如果組件同時具有強式名稱和軟體發行者身分識別，則會使用軟體發行者身分識別。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-113">If an assembly has both a strong name and a software publisher identity, then the software publisher identity is used.</span></span> <span data-ttu-id="f1b4c-114">如果組件來自網際網路，且未經過簽署，則會使用 URL 識別。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-114">If the assembly comes from the Internet and is unsigned, the URL identity is used.</span></span> <span data-ttu-id="f1b4c-115">如需有關組件和強式名稱的詳細資訊，請參閱[使用組件進行設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-115">For more information about assemblies and strong names, see [Programming with Assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md).</span></span>  
  
- <span data-ttu-id="f1b4c-116">漫遊存放區會與具有漫遊使用者設定檔的使用者一起移動。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-116">Roaming stores move with a user that has a roaming user profile.</span></span> <span data-ttu-id="f1b4c-117">檔案會寫入網路目錄，且會下載到使用者登入的任何電腦。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-117">Files are written to a network directory and are downloaded to any computer the user logs into.</span></span> <span data-ttu-id="f1b4c-118">如需有關漫遊使用者設定檔的詳細資訊，請參閱 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-118">For more information about roaming user profiles, see <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f1b4c-119">隔離儲存區可以透過結合使用者、網域和組件身分識別的概念，以下列方式隔離資料，且每個方式都有自己的使用案例：</span><span class="sxs-lookup"><span data-stu-id="f1b4c-119">By combining the concepts of user, domain, and assembly identity, isolated storage can isolate data in the following ways, each of which has its own usage scenarios:</span></span>  
  
- [<span data-ttu-id="f1b4c-120">依使用者和組件隔離</span><span class="sxs-lookup"><span data-stu-id="f1b4c-120">Isolation by user and assembly</span></span>](#UserAssembly)  
  
- [<span data-ttu-id="f1b4c-121">依使用者、網域和組件隔離</span><span class="sxs-lookup"><span data-stu-id="f1b4c-121">Isolation by user, domain, and assembly</span></span>](#UserDomainAssembly)  
  
 <span data-ttu-id="f1b4c-122">這些隔離中，任一個都可以與漫遊使用者設定檔結合。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-122">Either of these isolations can be combined with a roaming user profile.</span></span> <span data-ttu-id="f1b4c-123">如需詳細資訊，請參閱[隔離儲存區和漫遊](#Roaming)一節。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-123">For more information, see the section [Isolated Storage and Roaming](#Roaming).</span></span>  
  
 <span data-ttu-id="f1b4c-124">下圖示範如何以不同的範圍隔離儲存區：</span><span class="sxs-lookup"><span data-stu-id="f1b4c-124">The following illustration demonstrates how stores are isolated in different scopes:</span></span>  
  
 ![顯示依使用者和組件隔離的圖表。](./media/types-of-isolation/isolated-storage-types.gif)  
  
 <span data-ttu-id="f1b4c-126">請注意，除了漫遊存放區之外，電腦一律以隱含方式將隔離儲存區隔離，因為它會使用指定電腦本機的儲存設施。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-126">Note that except for roaming stores, isolated storage is always implicitly isolated by computer because it uses the storage facilities that are local to a given computer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f1b4c-127">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式無法使用隔離儲存區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-127">Isolated storage is not available for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="f1b4c-128">請改用 Windows 執行階段 API 所提供的 `Windows.Storage` 命名空間來儲存本機資料與檔案。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-128">Instead, use the application data classes in the `Windows.Storage` namespaces included in the Windows Runtime API to store local data and files.</span></span> <span data-ttu-id="f1b4c-129">如需詳細資訊，請參閱 Windows 開發人員中心的 [應用程式資料](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) 。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-129">For more information, see [Application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) in the Windows Dev Center.</span></span>  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a><span data-ttu-id="f1b4c-130">依使用者和組件隔離</span><span class="sxs-lookup"><span data-stu-id="f1b4c-130">Isolation by User and Assembly</span></span>  
 <span data-ttu-id="f1b4c-131">當使用資料存放區的組件必須從任何應用程式的網域存取時，則適用依使用者和組件隔離。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-131">When the assembly that uses the data store needs to be accessible from any application's domain, isolation by user and assembly is appropriate.</span></span> <span data-ttu-id="f1b4c-132">在此情況下，隔離儲存區通常用來儲存適用於多個應用程式，且未繫結至任何特定應用程式的資料，例如使用者的名稱或授權資訊。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-132">Typically, in this situation, isolated storage is used to store data that applies across multiple applications and is not tied to any particular application, such as the user's name or license information.</span></span> <span data-ttu-id="f1b4c-133">若要存取依使用者和組件隔離的儲存區，程式碼必須受到信任，才能在應用程式之間傳輸資訊。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-133">To access storage isolated by user and assembly, code must be trusted to transfer information between applications.</span></span> <span data-ttu-id="f1b4c-134">依使用者和組件隔離通常可以在內部網路上進行，但無法在網際網路上進行。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-134">Typically, isolation by user and assembly is allowed on intranets but not on the Internet.</span></span> <span data-ttu-id="f1b4c-135">呼叫靜態 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> 方法，並傳入使用者和組件 <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 會傳回具有這種隔離的儲存區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-135">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> method and passing in a user and an assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="f1b4c-136">下列程式碼範例會擷取依使用者和組件隔離的存放區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-136">The following code example retrieves a store that is isolated by user and assembly.</span></span> <span data-ttu-id="f1b4c-137">您可以透過 `isoFile` 物件存取這個存放區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-137">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 <span data-ttu-id="f1b4c-138">如需使用辨識項參數的範例，請參閱 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-138">For an example that uses the evidence parameters, see <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.</span></span>  
  
 <span data-ttu-id="f1b4c-139"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> 方法可以當作捷徑使用，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-139">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="f1b4c-140">此捷徑無法用來開啟能夠漫遊的存放區；在此情況下，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-140">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a><span data-ttu-id="f1b4c-141">依使用者、網域和組件隔離</span><span class="sxs-lookup"><span data-stu-id="f1b4c-141">Isolation by User, Domain, and Assembly</span></span>  
 <span data-ttu-id="f1b4c-142">如果您的應用程式使用需要私人資料存放區的協力廠商組件，您可以使用隔離儲存區來儲存私人資料。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-142">If your application uses a third-party assembly that requires a private data store, you can use isolated storage to store the private data.</span></span> <span data-ttu-id="f1b4c-143">依使用者、網域和組件隔離可確保只有指定之組件中的程式碼可以存取資料，而且只有在組件由建立存放區時所執行的應用程式使用的情況下，以及只有在建立存放區之使用者執行應用程式的情況下，才可以存取。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-143">Isolation by user, domain, and assembly ensures that only code in a given assembly can access the data, and only when the assembly is used by the application that was running when the assembly created the store, and only when the user for whom the store was created runs the application.</span></span> <span data-ttu-id="f1b4c-144">依使用者、網域和組件隔離可防止協力廠商組件向其他應用程式洩漏資料。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-144">Isolation by user, domain, and assembly keeps the third-party assembly from leaking data to other applications.</span></span> <span data-ttu-id="f1b4c-145">如果您知道您想要使用隔離儲存區，但不確定要使用哪一種隔離，這種隔離類型應該是預設選擇。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-145">This isolation type should be your default choice if you know that you want to use isolated storage but are not sure which type of isolation to use.</span></span> <span data-ttu-id="f1b4c-146">呼叫 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 的靜態 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法，並傳入使用者、網域和組件 <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 會傳回具有這種隔離的儲存區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-146">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> and passing in a user, domain, and assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="f1b4c-147">下列程式碼範例會擷取依使用者、網域和組件隔離的存放區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-147">The following code example retrieves a store isolated by user, domain, and assembly.</span></span> <span data-ttu-id="f1b4c-148">您可以透過 `isoFile` 物件存取這個存放區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-148">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 <span data-ttu-id="f1b4c-149">另一種方法可以當作捷徑使用，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-149">Another method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="f1b4c-150">此捷徑無法用來開啟能夠漫遊的存放區；在此情況下，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-150">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a><span data-ttu-id="f1b4c-151">隔離儲存區和漫遊</span><span class="sxs-lookup"><span data-stu-id="f1b4c-151">Isolated Storage and Roaming</span></span>  
 <span data-ttu-id="f1b4c-152">漫遊使用者設定檔是 Windows 的一個功能，可讓使用者設定網路上的身分識別，並使用該身分識別登入任何網路電腦，讓所有個人化設定繼續存在。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-152">Roaming user profiles are a Windows feature that enables a user to set up an identity on a network and use that identity to log into any network computer, carrying over all personalized settings.</span></span> <span data-ttu-id="f1b4c-153">使用隔離儲存區的組件可以指定使用者的隔離儲存區應該隨著漫遊使用者設定檔移動。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-153">An assembly that uses isolated storage can specify that the user's isolated storage should move with the roaming user profile.</span></span> <span data-ttu-id="f1b4c-154">漫遊可以搭配依使用者和組件隔離，或依使用者、網域和組件隔離使用。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-154">Roaming can be used in conjunction with isolation by user and assembly or with isolation by user, domain, and assembly.</span></span> <span data-ttu-id="f1b4c-155">如果未使用漫遊範圍，即使使用漫遊使用者設定檔，存放區也將不會漫遊。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-155">If a roaming scope is not used, stores will not roam even if a roaming user profile is used.</span></span>  
  
 <span data-ttu-id="f1b4c-156">下列程式碼範例會擷取依使用者和組件隔離的漫遊存放區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-156">The following code example retrieves a roaming store isolated by user and assembly.</span></span> <span data-ttu-id="f1b4c-157">您可以透過 `isoFile` 物件存取這個存放區。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-157">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 <span data-ttu-id="f1b4c-158">若要建立依使用者、網域和應用程式隔離的漫遊存放區，可以新增網域範圍。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-158">A domain scope can be added to create a roaming store isolated by user, domain, and application.</span></span> <span data-ttu-id="f1b4c-159">下列程式碼範例示範此工作。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-159">The following code example demonstrates this.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="f1b4c-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1b4c-160">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="f1b4c-161">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="f1b4c-161">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
