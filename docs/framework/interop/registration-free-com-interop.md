---
title: 免註冊的 COM Interop
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a3de327001f987b6c35d547b7cf3cbe7feeac49
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648517"
---
# <a name="registration-free-com-interop"></a><span data-ttu-id="5f6e4-102">免註冊的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="5f6e4-102">Registration-Free COM Interop</span></span>
<span data-ttu-id="5f6e4-103">免註冊的 COM Interop 不需要使用 Windows 登錄來儲存組件資訊，即可啟動元件。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-103">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="5f6e4-104">您不是在部署期間在電腦上登錄元件，而是在設計階段建立 Win32 樣式資訊清單檔案，其中包含繫結和啟動的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-104">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="5f6e4-105">這些資訊清單檔案 (而不是登錄機碼) 會引導物件的啟動。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-105">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="5f6e4-106">為您的組件使用免註冊啟動，而不是在部署期間將其註冊，有兩個優點：</span><span class="sxs-lookup"><span data-stu-id="5f6e4-106">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
- <span data-ttu-id="5f6e4-107">當電腦上安裝多個 DLL 版本時，您可以控制要啟動哪個版本。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-107">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
- <span data-ttu-id="5f6e4-108">終端使用者可以使用 XCOPY 或 FTP，將您的應用程式複製到他們電腦上的適當目錄。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-108">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="5f6e4-109">接著便可從該目錄執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-109">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="5f6e4-110">本節說明免註冊 COM Interop 所需的兩種資訊清單類型：應用程式和元件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-110">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="5f6e4-111">這些資訊清單是 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-111">These manifests are XML files.</span></span> <span data-ttu-id="5f6e4-112">應用程式資訊清單是由應用程式開發人員建立，其中包含說明組件和組件相依性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-112">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="5f6e4-113">元件資訊清單是由元件開發人員建立，其中包含其他位在 Windows 登錄中的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-113">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="5f6e4-114">免註冊 COM Interop 的需求</span><span class="sxs-lookup"><span data-stu-id="5f6e4-114">Requirements for registration-free COM interop</span></span>  
  
1. <span data-ttu-id="5f6e4-115">對免註冊 COM Interop 的支援，會依據程式庫組件的類型而稍微不同；具體來說，就是組件為 Unmanaged (COM 並存) 或 Managed (.NET 架構)。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-115">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="5f6e4-116">下表顯示各組件類型的作業系統和 .NET Framework 版本需求。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-116">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="5f6e4-117">組件類型</span><span class="sxs-lookup"><span data-stu-id="5f6e4-117">Assembly type</span></span>|<span data-ttu-id="5f6e4-118">作業系統</span><span class="sxs-lookup"><span data-stu-id="5f6e4-118">Operating system</span></span>|<span data-ttu-id="5f6e4-119">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="5f6e4-119">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="5f6e4-120">COM 並存</span><span class="sxs-lookup"><span data-stu-id="5f6e4-120">COM side-by-side</span></span>|<span data-ttu-id="5f6e4-121">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="5f6e4-121">Microsoft Windows XP</span></span>|<span data-ttu-id="5f6e4-122">不需要。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-122">Not required.</span></span>|  
    |<span data-ttu-id="5f6e4-123">.NET 架構</span><span class="sxs-lookup"><span data-stu-id="5f6e4-123">.NET-based</span></span>|<span data-ttu-id="5f6e4-124">Windows XP 含 SP2</span><span class="sxs-lookup"><span data-stu-id="5f6e4-124">Windows XP with SP2</span></span>|<span data-ttu-id="5f6e4-125">NET Framework 1.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-125">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="5f6e4-126">Windows Server 2003 系列也支援適用於 .NET 架構組件的免註冊 COM Interop。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-126">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="5f6e4-127">若要使 .NET 架構的類別相容於來自 COM 的免註冊啟動，該類別必須要有預設建構函式，而且必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-127">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a default constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="5f6e4-128">設定適用於免註冊啟動的 COM 元件</span><span class="sxs-lookup"><span data-stu-id="5f6e4-128">Configuring COM components for registration-free activation</span></span>  
  
1. <span data-ttu-id="5f6e4-129">若要讓 COM 元件參與免註冊啟動，必須將其部署為並存組件。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-129">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="5f6e4-130">並存組件是 Unmanaged 組件。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-130">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="5f6e4-131">如需詳細資訊，請參閱[使用並存組件](/windows/desktop/SbsCs/using-side-by-side-assemblies) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-131">For more information, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
     <span data-ttu-id="5f6e4-132">若要使用 COM 並存組件，.NET 架構應用程式開發人員必須提供應用程式資訊清單，其中包含繫結和啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-132">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="5f6e4-133">對 Unmanaged 並存組件的支援內建在 Windows XP 作業系統中。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-133">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="5f6e4-134">當所要啟動的元件不在登錄中時，COM 執行階段 (作業系統可支援) 會掃描應用程式資訊清單，以取得啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-134">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="5f6e4-135">針對安裝在 Windows XP 上的 COM 元件，免註冊啟動是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-135">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="5f6e4-136">如需將並存組件加入至應用程式的詳細指示，請參閱[使用並存組件](/windows/desktop/SbsCs/using-side-by-side-assemblies) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-136">For detailed instructions on adding a side-by-side assembly to an application, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f6e4-137">並存執行是 .NET Framework 的功能，可讓多版執行階段，以及使用某版執行階段的多版應用程式和元件，同時在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-137">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="5f6e4-138">並存執行和並存組件是提供並行功能的不同機制。</span><span class="sxs-lookup"><span data-stu-id="5f6e4-138">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f6e4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f6e4-139">See also</span></span>

- [<span data-ttu-id="5f6e4-140">如何：設定免註冊啟用的 .NET Framework 架構 COM 元件</span><span class="sxs-lookup"><span data-stu-id="5f6e4-140">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
