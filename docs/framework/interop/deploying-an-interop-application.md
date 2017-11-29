---
title: "部署 Interop 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f804843c248e0051582aca6d1dd6328871e1cc06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-an-interop-application"></a><span data-ttu-id="a415c-102">部署 Interop 應用程式</span><span class="sxs-lookup"><span data-stu-id="a415c-102">Deploying an Interop Application</span></span>
<span data-ttu-id="a415c-103">Interop 應用程式通常包含 .NET 用戶端組件、代表各種不同 COM 型別程式庫的一或多個 Interop 組件，以及一或多個已登錄的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="a415c-103">An interop application typically includes a .NET client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span> <span data-ttu-id="a415c-104">Visual Studio 和 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供工具以匯入型別程式庫，並將它轉換成 Interop 組件，如[匯入型別程式庫作為組件](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="a415c-104">Visual Studio and the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provide tools to import and convert a type library to an interop assembly, as discussed in [Importing a Type Library as an Assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span></span> <span data-ttu-id="a415c-105">有兩種方式可以部署 Interop 應用程式：</span><span class="sxs-lookup"><span data-stu-id="a415c-105">There are two ways to deploy an interop application:</span></span>  
  
-   <span data-ttu-id="a415c-106">使用內嵌的 Interop 類型：從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，您可以指示編譯器將 Interop 組件的類型資訊內嵌到可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a415c-106">By using embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="a415c-107">編譯器只會內嵌應用程式使用的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="a415c-107">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="a415c-108">您不必與應用程式一起部署 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="a415c-108">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="a415c-109">這是建議使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="a415c-109">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="a415c-110">透過部署 Interop 組件：您可以建立 Interop 組件的標準參考。</span><span class="sxs-lookup"><span data-stu-id="a415c-110">By deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="a415c-111">在此情況下，Interop 組件必須與您的應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="a415c-111">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="a415c-112">如果您運用這項技巧，但不使用私用的 COM 元件，請一律參考 COM 元件作者發佈的主要 Interop 組件 (PIA)，這是您想要併入 Managed 程式碼的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="a415c-112">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="a415c-113">如需製作和使用主要 Interop 組件的詳細資訊，請參閱[主要 Interop 組件](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080)。</span><span class="sxs-lookup"><span data-stu-id="a415c-113">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).</span></span>  
  
 <span data-ttu-id="a415c-114">如果您使用內嵌的 Interop 類型，部署就會簡單且直接。</span><span class="sxs-lookup"><span data-stu-id="a415c-114">If you use embedded interop types, deployment is simple and straightforward.</span></span> <span data-ttu-id="a415c-115">您不需要特別做什麼。</span><span class="sxs-lookup"><span data-stu-id="a415c-115">There is nothing special you need to do.</span></span> <span data-ttu-id="a415c-116">這篇文章的其餘部分會說明部署 Interop 組件和您應用程式的狀況。</span><span class="sxs-lookup"><span data-stu-id="a415c-116">The rest of this article describes the scenarios for deploying interop assemblies with your application.</span></span>  
  
## <a name="deploying-interop-assemblies"></a><span data-ttu-id="a415c-117">部署 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="a415c-117">Deploying Interop Assemblies</span></span>  
 <span data-ttu-id="a415c-118">組件可以有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="a415c-118">Assemblies can have strong names.</span></span> <span data-ttu-id="a415c-119">強式名稱組件包含發行者的公開金鑰，這會提供唯一識別。</span><span class="sxs-lookup"><span data-stu-id="a415c-119">A strong-named assembly includes the publisher's public key, which provides a unique identity.</span></span> <span data-ttu-id="a415c-120">[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 所產生的組件可由發行者使用 **/keyfile** 選項簽署。</span><span class="sxs-lookup"><span data-stu-id="a415c-120">Assemblies that are produced by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) can be signed by the publisher by using the **/keyfile** option.</span></span> <span data-ttu-id="a415c-121">您可以將已簽署的組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="a415c-121">You can install signed assemblies into the global assembly cache.</span></span> <span data-ttu-id="a415c-122">未簽署的組件必須安裝在使用者電腦上，當成私用組件。</span><span class="sxs-lookup"><span data-stu-id="a415c-122">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
### <a name="private-assemblies"></a><span data-ttu-id="a415c-123">私用組件</span><span class="sxs-lookup"><span data-stu-id="a415c-123">Private Assemblies</span></span>  
 <span data-ttu-id="a415c-124">若要安裝供私人使用的組件，應用程式可執行檔和包含已匯入 COM 類型的 Interop 組件，都必須以相同的目錄結構安裝。</span><span class="sxs-lookup"><span data-stu-id="a415c-124">To install an assembly to be used privately, both the application executable and the interop assembly that contains imported COM types must be installed in the same directory structure.</span></span> <span data-ttu-id="a415c-125">下圖顯示供 Client1.exe 和 Client2.exe 私下使用的未簽署 Interop 組件，它們位在不同的應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="a415c-125">The following illustration shows an unsigned interop assembly to be used privately by Client1.exe and Client2.exe, which reside in separate application directories.</span></span> <span data-ttu-id="a415c-126">本例中稱之為 LOANLib.dll 的 Interop 組件，安裝了兩次。</span><span class="sxs-lookup"><span data-stu-id="a415c-126">The interop assembly, which is called LOANLib.dll in this example, is installed twice.</span></span>  
  
 <span data-ttu-id="a415c-127">![目錄結構和 Windows 登錄](../../../docs/framework/interop/media/comdeployprivate.gif "comdeployprivate")</span><span class="sxs-lookup"><span data-stu-id="a415c-127">![Directory structure and Windows registry](../../../docs/framework/interop/media/comdeployprivate.gif "comdeployprivate")</span></span>  
<span data-ttu-id="a415c-128">私用部署的目錄結構和登錄項目</span><span class="sxs-lookup"><span data-stu-id="a415c-128">Directory structure and registry entries for a private deployment</span></span>  
  
 <span data-ttu-id="a415c-129">與應用程式建立關聯的所有 COM 元件都必須都安裝在 Windows 登錄中。</span><span class="sxs-lookup"><span data-stu-id="a415c-129">All COM components associated with the application must be installed in the Windows registry.</span></span> <span data-ttu-id="a415c-130">如果圖中的 Client1.exe 和 Client2.exe 安裝在不同的電腦上，您必須在兩部電腦上都登錄 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="a415c-130">If Client1.exe and Client2.exe in the illustration are installed on different computers, you must register the COM components on both computers.</span></span>  
  
### <a name="shared-assemblies"></a><span data-ttu-id="a415c-131">共用組件</span><span class="sxs-lookup"><span data-stu-id="a415c-131">Shared Assemblies</span></span>  
 <span data-ttu-id="a415c-132">多個應用程式共用的組件應該安裝在稱為全域組件快取的集中式存放庫中。</span><span class="sxs-lookup"><span data-stu-id="a415c-132">Assemblies that are shared by multiple applications should be installed in a centralized repository called the global assembly cache.</span></span> <span data-ttu-id="a415c-133">.NET 用戶端可以存取相同的 Interop 組件複本，它是簽署並安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="a415c-133">.NET clients can access the same copy of the interop assembly, which is signed and installed in the global assembly cache.</span></span> <span data-ttu-id="a415c-134">如需產生和使用主要 Interop 組件的詳細資訊，請參閱[主要 Interop 組件](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080)。</span><span class="sxs-lookup"><span data-stu-id="a415c-134">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a415c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a415c-135">See Also</span></span>  
 [<span data-ttu-id="a415c-136">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a415c-136">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="a415c-137">匯入型別程式庫作為組件</span><span class="sxs-lookup"><span data-stu-id="a415c-137">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="a415c-138">在 Managed 程式碼中使用 COM 類型</span><span class="sxs-lookup"><span data-stu-id="a415c-138">Using COM Types in Managed Code</span></span>](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [<span data-ttu-id="a415c-139">編譯 Interop 專案</span><span class="sxs-lookup"><span data-stu-id="a415c-139">Compiling an Interop Project</span></span>](../../../docs/framework/interop/compiling-an-interop-project.md)
