---
title: 與非受控程式碼交互操作
description: 使用非受控碼來檢查互通性。 CLR 會向用戶端和伺服器隱藏 .NET 元件和非受控碼的物件模型有何不同。
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
ms.openlocfilehash: 1cebd75907fd202715cb337593186d248107bdbb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621869"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="adfeb-104">與非受控程式碼交互操作</span><span class="sxs-lookup"><span data-stu-id="adfeb-104">Interoperating with unmanaged code</span></span>

<span data-ttu-id="adfeb-105">.NET Framework 可促進與 COM 元件、COM+ 服務、外部型別程式庫和許多作業系統服務進行的互動。</span><span class="sxs-lookup"><span data-stu-id="adfeb-105">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="adfeb-106">資料類型、方法簽章和錯誤處理機制因 Managed 和 Unmanaged 物件模型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="adfeb-106">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="adfeb-107">為了簡化 .NET Framework 元件與 Unmanaged 程式碼之間的互通性，以及簡化移轉路徑，通用語言執行平台會對用戶端與伺服器隱匿這些物件模型中的差異。</span><span class="sxs-lookup"><span data-stu-id="adfeb-107">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="adfeb-108">在執行階段的控制之下執行的程式碼稱為 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="adfeb-108">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="adfeb-109">相反地，在執行階段外部執行的程式碼稱為 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="adfeb-109">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="adfeb-110">COM 元件、ActiveX 介面及 Windows API 函式都是 Unmanaged 程式碼的範例。</span><span class="sxs-lookup"><span data-stu-id="adfeb-110">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="adfeb-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="adfeb-111">In this section</span></span>

[<span data-ttu-id="adfeb-112">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="adfeb-112">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="adfeb-113">描述如何從 .NET Framework 應用程式使用 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="adfeb-113">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="adfeb-114">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="adfeb-114">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="adfeb-115">描述如何從 COM 應用程式使用 .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="adfeb-115">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="adfeb-116">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="adfeb-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="adfeb-117">描述如何使用平台叫用呼叫 Unmanaged DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="adfeb-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="adfeb-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="adfeb-118">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="adfeb-119">描述適用於 COM Interop 和平台叫用的封送處理。</span><span class="sxs-lookup"><span data-stu-id="adfeb-119">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="adfeb-120">作法：對應 HRESULT 和例外狀況</span><span class="sxs-lookup"><span data-stu-id="adfeb-120">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="adfeb-121">描述例外狀況與 HRESULT 之間的對應。</span><span class="sxs-lookup"><span data-stu-id="adfeb-121">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="adfeb-122">類型等價和內嵌 Interop 類型</span><span class="sxs-lookup"><span data-stu-id="adfeb-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="adfeb-123">描述如何將 COM 類型的類型資訊內嵌於組件，以及通用語言執行平台如何決定內嵌 COM 類型的對等項。</span><span class="sxs-lookup"><span data-stu-id="adfeb-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="adfeb-124">作法：使用 Tlbimp.exe 產生主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="adfeb-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="adfeb-125">描述如何使用 *Tlbimp.exe* (類型程式庫匯入工具) 產生主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="adfeb-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="adfeb-126">作法：登錄主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="adfeb-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="adfeb-127">描述如何註冊主要 Interop 組件，以便您能在專案中加以參考。</span><span class="sxs-lookup"><span data-stu-id="adfeb-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="adfeb-128">免註冊的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="adfeb-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="adfeb-129">描述 COM Interop 如何在不使用 Windows 登錄的情況下啟動元件。</span><span class="sxs-lookup"><span data-stu-id="adfeb-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="adfeb-130">作法：設定 .NET Framework 架構 COM 元件進行免註冊啟用</span><span class="sxs-lookup"><span data-stu-id="adfeb-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="adfeb-131">描述如何建立應用程式資訊清單，以及如何建立和內嵌元件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="adfeb-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="adfeb-132">相關章節</span><span class="sxs-lookup"><span data-stu-id="adfeb-132">Related sections</span></span>

[<span data-ttu-id="adfeb-133">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="adfeb-133">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="adfeb-134">描述由 COM Interop 所提供的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="adfeb-134">Describes the wrappers provided by COM interop.</span></span>
