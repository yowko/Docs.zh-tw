---
title: "隔離的類型"
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
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6b07c090a381925f5330a820214126a121d3790b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-isolation"></a><span data-ttu-id="a7b4e-102">隔離的類型</span><span class="sxs-lookup"><span data-stu-id="a7b4e-102">Types of Isolation</span></span>
<span data-ttu-id="a7b4e-103">存取隔離儲存區永遠僅限於建立它之使用者的。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-103">Access to isolated storage is always restricted to the user who created it.</span></span> <span data-ttu-id="a7b4e-104">若要實作這種類型的隔離，通用語言執行平台使用相同作業系統辨識出的使用者身分識別的概念與開啟存放區時，程式碼執行所在的處理序相關聯的識別。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-104">To implement this type of isolation, the common language runtime uses the same notion of user identity that the operating system recognizes, which is the identity associated with the process in which the code is running when the store is opened.</span></span> <span data-ttu-id="a7b4e-105">這個身分識別是一個已驗證的使用者的身分識別，但是模擬可能會以動態方式變更目前使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-105">This identity is an authenticated user identity, but impersonation can cause the identity of the current user to change dynamically.</span></span>  
  
 <span data-ttu-id="a7b4e-106">存取隔離儲存區也是根據與應用程式定義域和組件，或單獨的組件相關聯的身分識別來限制。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-106">Access to isolated storage is also restricted according to the identity associated with the application's domain and assembly, or with the assembly alone.</span></span> <span data-ttu-id="a7b4e-107">執行階段會以下列方式取得這些身分識別：</span><span class="sxs-lookup"><span data-stu-id="a7b4e-107">The runtime obtains these identities in the following ways:</span></span>  
  
-   <span data-ttu-id="a7b4e-108">定義域識別代表應用程式，這在 web 應用程式的情況下可能會是完整的 URL 辨識的項。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-108">Domain identity represents the evidence of the application, which in the case of a web application might be the full URL.</span></span> <span data-ttu-id="a7b4e-109">殼層裝載程式碼的定義域識別可能會根據應用程式的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-109">For shell-hosted code, the domain identity might be based on the application directory path.</span></span> <span data-ttu-id="a7b4e-110">例如，如果可執行檔將會從路徑 C:\Office\MyApp.exe 網域身分識別將 C:\Office\MyApp.exe。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-110">For example, if the executable runs from the path C:\Office\MyApp.exe, the domain identity would be C:\Office\MyApp.exe.</span></span>  
  
-   <span data-ttu-id="a7b4e-111">組件的辨識項組件識別。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-111">Assembly identity is the evidence of the assembly.</span></span> <span data-ttu-id="a7b4e-112">這可能來自於密碼編譯數位簽章，它可以是組件的[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)，組件或它的 URL 識別的軟體發行者。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-112">This might come from a cryptographic digital signature, which can be the assembly's [strong name](../../../docs/framework/app-domains/strong-named-assemblies.md), the software publisher of the assembly, or its URL identity.</span></span> <span data-ttu-id="a7b4e-113">如果組件具有強式名稱和軟體發行者身分識別，則會使用軟體發行者身分識別。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-113">If an assembly has both a strong name and a software publisher identity, then the software publisher identity is used.</span></span> <span data-ttu-id="a7b4e-114">如果組件來自網際網路，且不帶正負號，將使用的 URL 識別。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-114">If the assembly comes from the Internet and is unsigned, the URL identity is used.</span></span> <span data-ttu-id="a7b4e-115">如需組件和強式名稱的詳細資訊，請參閱[使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-115">For more information about assemblies and strong names, see [Programming with Assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md).</span></span>  
  
-   <span data-ttu-id="a7b4e-116">漫遊存放區移動與使用者具有漫遊使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-116">Roaming stores move with a user that has a roaming user profile.</span></span> <span data-ttu-id="a7b4e-117">檔案會寫入至網路目錄，並會下載到任何電腦在使用者登入。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-117">Files are written to a network directory and are downloaded to any computer the user logs into.</span></span> <span data-ttu-id="a7b4e-118">如需漫遊使用者設定檔的詳細資訊，請參閱<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-118">For more information about roaming user profiles, see <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a7b4e-119">藉由結合使用者、 定義域和組件識別的概念，隔離儲存區可以隔離資料，在下列方面，每一個都有它自己的使用案例：</span><span class="sxs-lookup"><span data-stu-id="a7b4e-119">By combining the concepts of user, domain, and assembly identity, isolated storage can isolate data in the following ways, each of which has its own usage scenarios:</span></span>  
  
-   [<span data-ttu-id="a7b4e-120">依據使用者和組件的隔離。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-120">Isolation by user and assembly</span></span>](#UserAssembly)  
  
-   [<span data-ttu-id="a7b4e-121">依據使用者、 定義域和組件的隔離。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-121">Isolation by user, domain, and assembly</span></span>](#UserDomainAssembly)  
  
 <span data-ttu-id="a7b4e-122">其中一個這些任一個都可以結合漫遊使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-122">Either of these isolations can be combined with a roaming user profile.</span></span> <span data-ttu-id="a7b4e-123">如需詳細資訊，請參閱下節[隔離儲存區並漫遊](#Roaming)。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-123">For more information, see the section [Isolated Storage and Roaming](#Roaming).</span></span>  
  
 <span data-ttu-id="a7b4e-124">下圖示範如何將存放區隔離在不同範圍中。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-124">The following illustration demonstrates how stores are isolated in different scopes.</span></span>  
  
 <span data-ttu-id="a7b4e-125">![依據使用者和組件的隔離](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")</span><span class="sxs-lookup"><span data-stu-id="a7b4e-125">![Isolation by user and assembly](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")</span></span>  
<span data-ttu-id="a7b4e-126">隔離儲存區的類型</span><span class="sxs-lookup"><span data-stu-id="a7b4e-126">Types of isolated storage</span></span>  
  
 <span data-ttu-id="a7b4e-127">請注意，除了漫遊存放區，隔離儲存區一律以隱含方式隔離的電腦因為它會使用指定的電腦本機的儲存體功能。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-127">Note that except for roaming stores, isolated storage is always implicitly isolated by computer because it uses the storage facilities that are local to a given computer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7b4e-128">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式無法使用隔離儲存區。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-128">Isolated storage is not available for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="a7b4e-129">請改用 `Windows.Storage` 應用程式開發介面內含的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 命名空間中的應用程式資料類別來儲存本機資料和檔案。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-129">Instead, use the application data classes in the `Windows.Storage` namespaces included in the [!INCLUDE[wrt](../../../includes/wrt-md.md)] API to store local data and files.</span></span> <span data-ttu-id="a7b4e-130">如需詳細資訊，請參閱 Windows 開發人員中心的 [應用程式資料](http://go.microsoft.com/fwlink/?LinkId=229175) 。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-130">For more information, see [Application data](http://go.microsoft.com/fwlink/?LinkId=229175) in the Windows Dev Center.</span></span>  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a><span data-ttu-id="a7b4e-131">依據使用者和組件的隔離。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-131">Isolation by User and Assembly</span></span>  
 <span data-ttu-id="a7b4e-132">當使用資料的組件儲存為可從任何應用程式定義域，依據使用者和組件的隔離是適當的需求。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-132">When the assembly that uses the data store needs to be accessible from any application's domain, isolation by user and assembly is appropriate.</span></span> <span data-ttu-id="a7b4e-133">通常，在此情況下，隔離儲存區用來儲存適用於多個應用程式，以及未繫結至任何特定的應用程式，例如使用者名稱或授權資訊的資料。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-133">Typically, in this situation, isolated storage is used to store data that applies across multiple applications and is not tied to any particular application, such as the user's name or license information.</span></span> <span data-ttu-id="a7b4e-134">若要存取使用者和組件所隔離儲存區，程式碼必須是受信任的應用程式之間傳輸資訊。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-134">To access storage isolated by user and assembly, code must be trusted to transfer information between applications.</span></span> <span data-ttu-id="a7b4e-135">一般而言，使用者和組件所隔離允許內部網路，但不是在網際網路上。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-135">Typically, isolation by user and assembly is allowed on intranets but not on the Internet.</span></span> <span data-ttu-id="a7b4e-136">呼叫靜態<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType>方法，並將使用者和組件<xref:System.IO.IsolatedStorage.IsolatedStorageScope>傳回與這種隔離的存放裝置。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-136">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> method and passing in a user and an assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="a7b4e-137">下列程式碼範例會擷取使用者和組件所隔離的存放區。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-137">The following code example retrieves a store that is isolated by user and assembly.</span></span> <span data-ttu-id="a7b4e-138">在存放區可以透過存取`isoFile`物件。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-138">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 <span data-ttu-id="a7b4e-139">如需使用辨識項參數的範例，請參閱<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-139">For an example that uses the evidence parameters, see <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.</span></span>  
  
 <span data-ttu-id="a7b4e-140"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>方法可做為快顯，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-140">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="a7b4e-141">這個捷徑不能用來開啟能夠漫遊; 的存放區使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>在此情況下。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-141">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a><span data-ttu-id="a7b4e-142">依據使用者、 定義域和組件的隔離。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-142">Isolation by User, Domain, and Assembly</span></span>  
 <span data-ttu-id="a7b4e-143">如果您的應用程式使用協力廠商組件需要私用資料存放區，您可以使用隔離儲存區來儲存的私用資料。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-143">If your application uses a third-party assembly that requires a private data store, you can use isolated storage to store the private data.</span></span> <span data-ttu-id="a7b4e-144">依據使用者、 定義域和組件的隔離，可確保只有指定的組件中的程式碼可以存取資料，和只有在組件由應用程式執行時建立的組件存放區，且只在的使用者存放區已建立其執行時，才 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-144">Isolation by user, domain, and assembly ensures that only code in a given assembly can access the data, and only when the assembly is used by the application that was running when the assembly created the store, and only when the user for whom the store was created runs the application.</span></span> <span data-ttu-id="a7b4e-145">依據使用者、 定義域和組件的隔離會保留不外洩資料給其他應用程式的協力廠商組件。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-145">Isolation by user, domain, and assembly keeps the third-party assembly from leaking data to other applications.</span></span> <span data-ttu-id="a7b4e-146">這個隔離類型應該是預設選擇，如果您知道您想要使用隔離儲存區，但不確定哪一種隔離使用。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-146">This isolation type should be your default choice if you know that you want to use isolated storage but are not sure which type of isolation to use.</span></span> <span data-ttu-id="a7b4e-147">呼叫靜態<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法<xref:System.IO.IsolatedStorage.IsolatedStorageFile>並傳入使用者、 定義域和組件<xref:System.IO.IsolatedStorage.IsolatedStorageScope>傳回與這種隔離的存放裝置。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-147">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> and passing in a user, domain, and assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="a7b4e-148">下列程式碼範例會擷取使用者、 定義域和組件所隔離的存放區。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-148">The following code example retrieves a store isolated by user, domain, and assembly.</span></span> <span data-ttu-id="a7b4e-149">在存放區可以透過存取`isoFile`物件。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-149">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 <span data-ttu-id="a7b4e-150">下列程式碼範例所示，請使用另一種方法。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-150">Another method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="a7b4e-151">這個捷徑不能用來開啟能夠漫遊; 的存放區使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>在此情況下。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-151">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a><span data-ttu-id="a7b4e-152">隔離儲存區並漫遊</span><span class="sxs-lookup"><span data-stu-id="a7b4e-152">Isolated Storage and Roaming</span></span>  
 <span data-ttu-id="a7b4e-153">漫遊使用者設定檔是 Windows 功能，可讓使用者設定網路上的身分識別，並使用該識別來登入的任何網路電腦，執行於所有的個人化設定。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-153">Roaming user profiles are a Windows feature that enables a user to set up an identity on a network and use that identity to log into any network computer, carrying over all personalized settings.</span></span> <span data-ttu-id="a7b4e-154">使用隔離儲存區的組件可以指定使用者的隔離儲存區應該與漫遊使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-154">An assembly that uses isolated storage can specify that the user's isolated storage should move with the roaming user profile.</span></span> <span data-ttu-id="a7b4e-155">漫遊可以連同依據使用者和組件的隔離或隔離使用由使用者、 定義域和組件。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-155">Roaming can be used in conjunction with isolation by user and assembly or with isolation by user, domain, and assembly.</span></span> <span data-ttu-id="a7b4e-156">如果未使用漫遊的範圍，將不會漫遊存放區，即使使用漫遊使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-156">If a roaming scope is not used, stores will not roam even if a roaming user profile is used.</span></span>  
  
 <span data-ttu-id="a7b4e-157">下列程式碼範例會擷取使用者和組件所隔離的漫遊存放區。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-157">The following code example retrieves a roaming store isolated by user and assembly.</span></span> <span data-ttu-id="a7b4e-158">在存放區可以透過存取`isoFile`物件。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-158">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 <span data-ttu-id="a7b4e-159">若要建立依據使用者、 定義域和應用程式隔離的漫遊存放區，可以加入網域範圍。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-159">A domain scope can be added to create a roaming store isolated by user, domain, and application.</span></span> <span data-ttu-id="a7b4e-160">下列程式碼範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-160">The following code example demonstrates this.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="a7b4e-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7b4e-161">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="a7b4e-162">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="a7b4e-162">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
