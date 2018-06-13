---
title: 與非受控程式碼交互操作
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 583cfb6e3a5145c6c0dfc82ec9ff64c6d87414ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389502"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="857ea-102">與非受控程式碼交互操作</span><span class="sxs-lookup"><span data-stu-id="857ea-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="857ea-103">.NET Framework 可促進與 COM 元件、COM+ 服務、外部型別程式庫和許多作業系統服務進行的互動。</span><span class="sxs-lookup"><span data-stu-id="857ea-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="857ea-104">資料類型、方法簽章和錯誤處理機制因 Managed 和 Unmanaged 物件模型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="857ea-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="857ea-105">為了簡化 .NET Framework 元件與 Unmanaged 程式碼之間的互通性，以及簡化移轉路徑，通用語言執行平台會對用戶端與伺服器隱匿這些物件模型中的差異。</span><span class="sxs-lookup"><span data-stu-id="857ea-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="857ea-106">在執行階段的控制之下執行的程式碼稱為 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="857ea-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="857ea-107">相反地，在執行階段外部執行的程式碼稱為 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="857ea-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="857ea-108">COM 元件、ActiveX 介面及 Win32 API 函式都是 Unmanaged 程式碼的範例。</span><span class="sxs-lookup"><span data-stu-id="857ea-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="857ea-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="857ea-109">In this section</span></span>

[<span data-ttu-id="857ea-110">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="857ea-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="857ea-111">描述如何從 .NET Framework 應用程式使用 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="857ea-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="857ea-112">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="857ea-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="857ea-113">描述如何從 COM 應用程式使用 .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="857ea-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="857ea-114">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="857ea-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="857ea-115">描述如何使用平台叫用呼叫 Unmanaged DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="857ea-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="857ea-116">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="857ea-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="857ea-117">描述適用於 COM Interop 和平台叫用的封送處理。</span><span class="sxs-lookup"><span data-stu-id="857ea-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="857ea-118">操作說明：對應 HRESULT 和例外狀況</span><span class="sxs-lookup"><span data-stu-id="857ea-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="857ea-119">描述例外狀況與 HRESULT 之間的對應。</span><span class="sxs-lookup"><span data-stu-id="857ea-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="857ea-120">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="857ea-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="857ea-121">描述由 COM Interop 所提供的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="857ea-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="857ea-122">類型等價和內嵌 Interop 類型</span><span class="sxs-lookup"><span data-stu-id="857ea-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="857ea-123">描述如何將 COM 類型的類型資訊內嵌於組件，以及通用語言執行平台如何決定內嵌 COM 類型的對等項。</span><span class="sxs-lookup"><span data-stu-id="857ea-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="857ea-124">如何：使用 Tlbimp.exe 產生主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="857ea-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="857ea-125">描述如何使用 *Tlbimp.exe* (類型程式庫匯入工具) 產生主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="857ea-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="857ea-126">如何：登錄主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="857ea-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="857ea-127">描述如何註冊主要 Interop 組件，以便您能在專案中加以參考。</span><span class="sxs-lookup"><span data-stu-id="857ea-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="857ea-128">免註冊的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="857ea-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="857ea-129">描述 COM Interop 如何在不使用 Windows 登錄的情況下啟動元件。</span><span class="sxs-lookup"><span data-stu-id="857ea-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="857ea-130">如何：設定免註冊啟用的 .NET Framework 架構 COM 元件</span><span class="sxs-lookup"><span data-stu-id="857ea-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="857ea-131">描述如何建立應用程式資訊清單，以及如何建立和內嵌元件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="857ea-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>
