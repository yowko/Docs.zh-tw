---
title: "與 Unmanaged 程式碼互通"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f475877bcb7a794d1a58ef9202735e016363678b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="40951-102">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="40951-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="40951-103">.NET Framework 可促進與 COM 元件、COM+ 服務、外部型別程式庫和許多作業系統服務進行的互動。</span><span class="sxs-lookup"><span data-stu-id="40951-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="40951-104">資料類型、方法簽章和錯誤處理機制因 Managed 和 Unmanaged 物件模型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="40951-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="40951-105">為了簡化 .NET Framework 元件與 Unmanaged 程式碼之間的互通性，以及簡化移轉路徑，通用語言執行平台會對用戶端與伺服器隱匿這些物件模型中的差異。</span><span class="sxs-lookup"><span data-stu-id="40951-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="40951-106">在執行階段的控制之下執行的程式碼稱為 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="40951-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="40951-107">相反地，在執行階段外部執行的程式碼稱為 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="40951-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="40951-108">COM 元件、ActiveX 介面及 Win32 API 函式都是 Unmanaged 程式碼的範例。</span><span class="sxs-lookup"><span data-stu-id="40951-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40951-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="40951-109">In This Section</span></span>  
 [<span data-ttu-id="40951-110">與 Unmanaged 程式碼交互操作的「如何」主題</span><span class="sxs-lookup"><span data-stu-id="40951-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="40951-111">提供概念文件中所有與 Unmanaged 程式碼交互操作之「如何」主題的連結。</span><span class="sxs-lookup"><span data-stu-id="40951-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="40951-112">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="40951-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="40951-113">描述如何從 .NET Framework 應用程式使用 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="40951-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="40951-114">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="40951-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="40951-115">描述如何從 COM 應用程式使用 .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="40951-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="40951-116">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="40951-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="40951-117">描述如何使用平台叫用呼叫 Unmanaged DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="40951-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="40951-118">交互操作的設計考量</span><span class="sxs-lookup"><span data-stu-id="40951-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="40951-119">提供撰寫整合式 COM 元件的秘訣。</span><span class="sxs-lookup"><span data-stu-id="40951-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="40951-120">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="40951-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="40951-121">描述適用於 COM Interop 和平台叫用的封送處理。</span><span class="sxs-lookup"><span data-stu-id="40951-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="40951-122">操作說明：對應 HRESULT 和例外狀況</span><span class="sxs-lookup"><span data-stu-id="40951-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="40951-123">描述例外狀況與 HRESULT 之間的對應。</span><span class="sxs-lookup"><span data-stu-id="40951-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="40951-124">使用泛型型別交互操作</span><span class="sxs-lookup"><span data-stu-id="40951-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="40951-125">描述泛型型別在 COM Interop 中使用時的行為。</span><span class="sxs-lookup"><span data-stu-id="40951-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40951-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="40951-126">Related Sections</span></span>  
 [<span data-ttu-id="40951-127">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="40951-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="40951-128">提供有關將 COM 元件納入 .NET Framework 應用程式的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="40951-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>
