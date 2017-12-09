---
title: "Interop 封送處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 381eccc42d5abb85cde618f4710f044f172295d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="interop-marshaling"></a><span data-ttu-id="1fa12-102">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="1fa12-102">Interop Marshaling</span></span>
<a name="top"></a> <span data-ttu-id="1fa12-103">Interop 封送處理會控制如何以方法引數傳遞資料，以及控制呼叫期間於 Managed 和 Unmanaged 記憶體之間的傳回值。</span><span class="sxs-lookup"><span data-stu-id="1fa12-103">Interop marshaling governs how data is passed in method arguments and return values between managed and unmanaged memory during calls.</span></span> <span data-ttu-id="1fa12-104">Interop 封送處理是由 Common Language Runtime 的封送處理服務所執行的執行階段活動。</span><span class="sxs-lookup"><span data-stu-id="1fa12-104">Interop marshaling is a run-time activity performed by the common language runtime's marshaling service.</span></span>  
  
 <span data-ttu-id="1fa12-105">大部分的資料類型在 Managed 和 Unmanaged 記憶體中有共通的表示。</span><span class="sxs-lookup"><span data-stu-id="1fa12-105">Most data types have common representations in both managed and unmanaged memory.</span></span> <span data-ttu-id="1fa12-106">Interop 封送處理器會為您處理這些類型。</span><span class="sxs-lookup"><span data-stu-id="1fa12-106">The interop marshaler handles these types for you.</span></span> <span data-ttu-id="1fa12-107">其他類型可能模稜兩可，或根本不會在 Managed 記憶體中表示。</span><span class="sxs-lookup"><span data-stu-id="1fa12-107">Other types can be ambiguous or not represented at all in managed memory.</span></span>  
  
 <span data-ttu-id="1fa12-108">模稜兩可的類型不是有多個對應到單一 Managed 類型的 Unmanaged 表示，就是遺漏類型資訊 (例如陣列的大小)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-108">An ambiguous type can have either multiple unmanaged representations that map to a single managed type, or missing type information, such as the size of an array.</span></span> <span data-ttu-id="1fa12-109">針對模稜兩可的類型，封送處理器會提供預設表示，以及替代表示 (其中有多個表示)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-109">For ambiguous types, the marshaler provides a default representation and alternative representations where multiple representations exist.</span></span> <span data-ttu-id="1fa12-110">您可以將有關如何封送處理模稜兩可類型的明確指示，提供給封送處理器。</span><span class="sxs-lookup"><span data-stu-id="1fa12-110">You can supply explicit instructions to the marshaler on how it is to marshal an ambiguous type.</span></span>  
  
 <span data-ttu-id="1fa12-111">本概觀包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="1fa12-111">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="1fa12-112">平台叫用和 COM Interop 模型</span><span class="sxs-lookup"><span data-stu-id="1fa12-112">Platform Invoke and COM Interop Models</span></span>](#platform_invoke_and_com_interop_models)  
  
-   [<span data-ttu-id="1fa12-113">封送處理和 COM Apartment</span><span class="sxs-lookup"><span data-stu-id="1fa12-113">Marshaling and COM Apartments</span></span>](#marshaling_and_com_apartments)  
  
-   [<span data-ttu-id="1fa12-114">封送處理遠端呼叫</span><span class="sxs-lookup"><span data-stu-id="1fa12-114">Marshaling Remote Calls</span></span>](#marshaling_remote_calls)  
  
-   [<span data-ttu-id="1fa12-115">相關主題</span><span class="sxs-lookup"><span data-stu-id="1fa12-115">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="1fa12-116">參考</span><span class="sxs-lookup"><span data-stu-id="1fa12-116">Reference</span></span>](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a><span data-ttu-id="1fa12-117">平台叫用和 COM Interop 模型</span><span class="sxs-lookup"><span data-stu-id="1fa12-117">Platform Invoke and COM Interop Models</span></span>  
 <span data-ttu-id="1fa12-118">Common Language Runtime 提供兩種與 Unmanaged 程式碼互通的機制：</span><span class="sxs-lookup"><span data-stu-id="1fa12-118">The common language runtime provides two mechanisms for interoperating with unmanaged code:</span></span>  
  
-   <span data-ttu-id="1fa12-119">平台叫用，可讓 Managed 程式碼呼叫 Unmanaged 程式庫所匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="1fa12-119">Platform invoke, which enables managed code to call functions exported from an unmanaged library.</span></span>  
  
-   <span data-ttu-id="1fa12-120">COM Interop，可讓 Managed 程式碼透過介面與元件物件模型 (COM) 物件互動。</span><span class="sxs-lookup"><span data-stu-id="1fa12-120">COM interop, which enables managed code to interact with Component Object Model (COM) objects through interfaces.</span></span>  
  
 <span data-ttu-id="1fa12-121">平台叫用和 COM Interop 都會使用 Interop 封送處理，正確地將方法引數在呼叫端和被呼叫端之間來回移動 (如有必要)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-121">Both platform invoke and COM interop use interop marshaling to accurately move method arguments between caller and callee and back, if required.</span></span> <span data-ttu-id="1fa12-122">如下圖所示，除非需要[回呼函式](../../../docs/framework/interop/callback-functions.md)，否則平台叫用方法呼叫會從 Managed 程式碼流向 Unmanaged 程式碼，但絕不會反向流回。</span><span class="sxs-lookup"><span data-stu-id="1fa12-122">As the following illustration shows, a platform invoke method call flows from managed to unmanaged code and never the other way, except when [callback functions](../../../docs/framework/interop/callback-functions.md) are involved.</span></span> <span data-ttu-id="1fa12-123">即使平台叫用呼叫只可以從 Managed 程式碼流向 Unmanaged 程式碼，資料還是可以當做輸入或輸出參數來進行雙向流動。</span><span class="sxs-lookup"><span data-stu-id="1fa12-123">Even though platform invoke calls can flow only from managed to unmanaged code, data can flow in both directions as input or output parameters.</span></span> <span data-ttu-id="1fa12-124">COM Interop 方法呼叫可以流向任一方向。</span><span class="sxs-lookup"><span data-stu-id="1fa12-124">COM interop method calls can flow in either direction.</span></span>  
  
 <span data-ttu-id="1fa12-125">![平台叫用](../../../docs/framework/interop/media/interopmarshaling.png "interopmarshaling")</span><span class="sxs-lookup"><span data-stu-id="1fa12-125">![Platform invoke](../../../docs/framework/interop/media/interopmarshaling.png "interopmarshaling")</span></span>  
<span data-ttu-id="1fa12-126">平台叫用和 COM Interop 呼叫流程</span><span class="sxs-lookup"><span data-stu-id="1fa12-126">Platform invoke and COM interop call flow</span></span>  
  
 <span data-ttu-id="1fa12-127">這兩種機制在最低層級會使用相同的 Interop 封送處理服務，但特定資料類型只受 COM Interop 或平台叫用支援。</span><span class="sxs-lookup"><span data-stu-id="1fa12-127">At the lowest level, both mechanisms use the same interop marshaling service; however, certain data types are supported exclusively by COM interop or platform invoke.</span></span> <span data-ttu-id="1fa12-128">如需詳細資料，請參閱[預設的封送處理行為](../../../docs/framework/interop/default-marshaling-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-128">For details, see [Default Marshaling Behavior](../../../docs/framework/interop/default-marshaling-behavior.md).</span></span>  
  
 [<span data-ttu-id="1fa12-129">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1fa12-129">Back to top</span></span>](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a><span data-ttu-id="1fa12-130">封送處理和 COM Apartment</span><span class="sxs-lookup"><span data-stu-id="1fa12-130">Marshaling and COM Apartments</span></span>  
 <span data-ttu-id="1fa12-131">Interop 封送處理器會在 Common Language Runtime 堆積和 Unmanaged 堆積之間封送處理資料。</span><span class="sxs-lookup"><span data-stu-id="1fa12-131">The interop marshaler marshals data between the common language runtime heap and the unmanaged heap.</span></span> <span data-ttu-id="1fa12-132">當呼叫端和被呼叫端無法在相同的資料執行個體上進行操作時，就會發生封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-132">Marshaling occurs whenever the caller and callee cannot operate on the same instance of data.</span></span> <span data-ttu-id="1fa12-133">即使呼叫端和被呼叫端擁有其自己的資料複本，Interop 封送處理器還是可以讓呼叫端和被呼叫端在相同的資料上進行操作。</span><span class="sxs-lookup"><span data-stu-id="1fa12-133">The interop marshaler makes it possible for the caller and callee to appear to be operating on the same data even if they have their own copy of the data.</span></span>  
  
 <span data-ttu-id="1fa12-134">COM 也有一個封送處理器，可在不同的 COM Apartment 或不同的 COM 處理序之間封送處理資料。</span><span class="sxs-lookup"><span data-stu-id="1fa12-134">COM also has a marshaler that marshals data between COM apartments or different COM processes.</span></span> <span data-ttu-id="1fa12-135">在相同 COM Apartment 中的 Managed 和 Unmanaged 程式碼之間呼叫時，只需要 Interop 封送處理器。</span><span class="sxs-lookup"><span data-stu-id="1fa12-135">When calling between managed and unmanaged code within the same COM apartment, the interop marshaler is the only marshaler involved.</span></span> <span data-ttu-id="1fa12-136">在不同 COM Apartment 或不同處理序中的 Managed 程式碼和 Unmanaged 程式碼之間呼叫時，則同時需要 Interop 封送處理器和 COM 封送處理器。</span><span class="sxs-lookup"><span data-stu-id="1fa12-136">When calling between managed code and unmanaged code in a different COM apartment or a different process, both the interop marshaler and the COM marshaler are involved.</span></span>  
  
### <a name="com-clients-and-managed-servers"></a><span data-ttu-id="1fa12-137">COM 用戶端和 Managed 伺服器</span><span class="sxs-lookup"><span data-stu-id="1fa12-137">COM Clients and Managed Servers</span></span>  
 <span data-ttu-id="1fa12-138">具有 [Regasm.exe (組件註冊工具)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 所註冊之類型程式庫的已匯出 Managed 伺服器，會將 `ThreadingModel` 登錄項目設定為 `Both`。</span><span class="sxs-lookup"><span data-stu-id="1fa12-138">An exported managed server with a type library registered by the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) has a `ThreadingModel` registry entry set to `Both`.</span></span> <span data-ttu-id="1fa12-139">這個值表示伺服器可在單一執行緒 Apartment (STA) 或多執行緒 Apartment (MTA) 中啟動。</span><span class="sxs-lookup"><span data-stu-id="1fa12-139">This value indicates that the server can be activated in a single-threaded apartment (STA) or a multithreaded apartment (MTA).</span></span> <span data-ttu-id="1fa12-140">伺服器物件是在與其呼叫端相同的 Apartment 中所建立，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="1fa12-140">The server object is created in the same apartment as its caller, as shown in the following table.</span></span>  
  
|<span data-ttu-id="1fa12-141">COM 用戶端</span><span class="sxs-lookup"><span data-stu-id="1fa12-141">COM client</span></span>|<span data-ttu-id="1fa12-142">.NET 伺服器</span><span class="sxs-lookup"><span data-stu-id="1fa12-142">.NET server</span></span>|<span data-ttu-id="1fa12-143">封送處理需求</span><span class="sxs-lookup"><span data-stu-id="1fa12-143">Marshaling requirements</span></span>|  
|----------------|-----------------|-----------------------------|  
|<span data-ttu-id="1fa12-144">STA</span><span class="sxs-lookup"><span data-stu-id="1fa12-144">STA</span></span>|<span data-ttu-id="1fa12-145">`Both` 變成 STA。</span><span class="sxs-lookup"><span data-stu-id="1fa12-145">`Both` becomes STA.</span></span>|<span data-ttu-id="1fa12-146">相同 Apartment 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-146">Same-apartment marshaling.</span></span>|  
|<span data-ttu-id="1fa12-147">MTA</span><span class="sxs-lookup"><span data-stu-id="1fa12-147">MTA</span></span>|<span data-ttu-id="1fa12-148">`Both` 變成 MTA。</span><span class="sxs-lookup"><span data-stu-id="1fa12-148">`Both` becomes MTA.</span></span>|<span data-ttu-id="1fa12-149">相同 Apartment 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-149">Same-apartment marshaling.</span></span>|  
  
 <span data-ttu-id="1fa12-150">由於用戶端和伺服器位於相同的 Apartment 中，因此 Interop 封送處理服務會自動處理所有資料封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-150">Because the client and server are in the same apartment, the interop marshaling service automatically handles all data marshaling.</span></span> <span data-ttu-id="1fa12-151">下圖顯示 Interop 封送處理服務在相同 COM 樣式 Apartment 內的 Managed 和 Unmanaged 堆積之間進行操作。</span><span class="sxs-lookup"><span data-stu-id="1fa12-151">The following illustration shows the interop marshaling service operating between managed and unmanaged heaps within the same COM-style apartment.</span></span>  
  
 <span data-ttu-id="1fa12-152">![Interop 封送處理](../../../docs/framework/interop/media/interopheap.gif "interopheap")</span><span class="sxs-lookup"><span data-stu-id="1fa12-152">![Interop marshaling](../../../docs/framework/interop/media/interopheap.gif "interopheap")</span></span>  
<span data-ttu-id="1fa12-153">相同 Apartment 封送處理流程</span><span class="sxs-lookup"><span data-stu-id="1fa12-153">Same-apartment marshaling process</span></span>  
  
 <span data-ttu-id="1fa12-154">如果您打算匯出 Managed 伺服器，請注意 COM 用戶端會決定伺服器的 Apartment。</span><span class="sxs-lookup"><span data-stu-id="1fa12-154">If you plan to export a managed server, be aware that the COM client determines the apartment of the server.</span></span> <span data-ttu-id="1fa12-155">由 MTA 中初始化的 COM 用戶端所呼叫的 Managed 伺服器必須確保執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="1fa12-155">A managed server called by a COM client initialized in an MTA must ensure thread safety.</span></span>  
  
### <a name="managed-clients-and-com-servers"></a><span data-ttu-id="1fa12-156">Managed 用戶端和 COM 伺服器</span><span class="sxs-lookup"><span data-stu-id="1fa12-156">Managed Clients and COM Servers</span></span>  
 <span data-ttu-id="1fa12-157">Managed 用戶端 Apartment 的預設值為 MTA；不過，.NET 用戶端的應用程式類型可以變更預設值。</span><span class="sxs-lookup"><span data-stu-id="1fa12-157">The default setting for managed client apartments is MTA; however, the application type of the .NET client can change the default setting.</span></span> <span data-ttu-id="1fa12-158">例如，[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 用戶端 Apartment 設定為 STA。</span><span class="sxs-lookup"><span data-stu-id="1fa12-158">For example, a [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] client apartment setting is STA.</span></span> <span data-ttu-id="1fa12-159">您可以使用 <xref:System.STAThreadAttribute?displayProperty=nameWithType>、<xref:System.MTAThreadAttribute?displayProperty=nameWithType>、<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> 屬性或 <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> 屬性，來檢查及變更 Managed 用戶端的 Apartment 設定。</span><span class="sxs-lookup"><span data-stu-id="1fa12-159">You can use the <xref:System.STAThreadAttribute?displayProperty=nameWithType>, the <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property, or the <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> property to examine and change the apartment setting of a managed client.</span></span>  
  
 <span data-ttu-id="1fa12-160">元件作者會設定 COM 伺服器的執行緒相似性。</span><span class="sxs-lookup"><span data-stu-id="1fa12-160">The author of the component sets the thread affinity of a COM server.</span></span> <span data-ttu-id="1fa12-161">下表顯示 .NET 用戶端和 COM 伺服器的 Apartment 設定組合，</span><span class="sxs-lookup"><span data-stu-id="1fa12-161">The following table shows the combinations of apartment settings for .NET clients and COM servers.</span></span> <span data-ttu-id="1fa12-162">並顯示組合所產生的封送處理需求。</span><span class="sxs-lookup"><span data-stu-id="1fa12-162">It also shows the resulting marshaling requirements for the combinations.</span></span>  
  
|<span data-ttu-id="1fa12-163">.NET 用戶端</span><span class="sxs-lookup"><span data-stu-id="1fa12-163">.NET client</span></span>|<span data-ttu-id="1fa12-164">COM 伺服器</span><span class="sxs-lookup"><span data-stu-id="1fa12-164">COM server</span></span>|<span data-ttu-id="1fa12-165">封送處理需求</span><span class="sxs-lookup"><span data-stu-id="1fa12-165">Marshaling requirements</span></span>|  
|-----------------|----------------|-----------------------------|  
|<span data-ttu-id="1fa12-166">MTA (預設值)</span><span class="sxs-lookup"><span data-stu-id="1fa12-166">MTA (default)</span></span>|<span data-ttu-id="1fa12-167">MTA</span><span class="sxs-lookup"><span data-stu-id="1fa12-167">MTA</span></span><br /><br /> <span data-ttu-id="1fa12-168">STA</span><span class="sxs-lookup"><span data-stu-id="1fa12-168">STA</span></span>|<span data-ttu-id="1fa12-169">Interop 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-169">Interop marshaling.</span></span><br /><br /> <span data-ttu-id="1fa12-170">Interop 和 COM 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-170">Interop and COM marshaling.</span></span>|  
|<span data-ttu-id="1fa12-171">STA</span><span class="sxs-lookup"><span data-stu-id="1fa12-171">STA</span></span>|<span data-ttu-id="1fa12-172">MTA</span><span class="sxs-lookup"><span data-stu-id="1fa12-172">MTA</span></span><br /><br /> <span data-ttu-id="1fa12-173">STA</span><span class="sxs-lookup"><span data-stu-id="1fa12-173">STA</span></span>|<span data-ttu-id="1fa12-174">Interop 和 COM 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-174">Interop and COM marshaling.</span></span><br /><br /> <span data-ttu-id="1fa12-175">Interop 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-175">Interop marshaling.</span></span>|  
  
 <span data-ttu-id="1fa12-176">當 Managed 用戶端和 Unmnaged 伺服器位於相同的 Apartment 中時，Interop 封送處理服務會處理所有資料封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-176">When a managed client and unmanaged server are in the same apartment, the interop marshaling service handles all data marshaling.</span></span> <span data-ttu-id="1fa12-177">不過，當用戶端和伺服器在不同的 Apartment 中初始化時，還需要 COM 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-177">However, when client and server are initialized in different apartments, COM marshaling is also required.</span></span> <span data-ttu-id="1fa12-178">下圖顯示跨 Apartment 呼叫的項目。</span><span class="sxs-lookup"><span data-stu-id="1fa12-178">The following illustration shows the elements of a cross-apartment call.</span></span>  
  
 <span data-ttu-id="1fa12-179">![COM 封送處理](../../../docs/framework/interop/media/singleprocessmultapt.gif "singleprocessmultapt")</span><span class="sxs-lookup"><span data-stu-id="1fa12-179">![COM marshaling](../../../docs/framework/interop/media/singleprocessmultapt.gif "singleprocessmultapt")</span></span>  
<span data-ttu-id="1fa12-180">.NET 用戶端和 COM 物件之間的跨 Apartment 呼叫</span><span class="sxs-lookup"><span data-stu-id="1fa12-180">Cross-apartment call between a .NET client and COM object</span></span>  
  
 <span data-ttu-id="1fa12-181">針對跨 Apartment 封送處理，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1fa12-181">For cross-apartment marshaling, you can do the following:</span></span>  
  
-   <span data-ttu-id="1fa12-182">接受跨 Apartment 封送處理的額外負荷，只有在許多呼叫跨界限時才會很明顯。</span><span class="sxs-lookup"><span data-stu-id="1fa12-182">Accept the overhead of the cross-apartment marshaling, which is noticeable only when there are many calls across the boundary.</span></span> <span data-ttu-id="1fa12-183">您必須註冊 COM 元件的類型程式庫，呼叫才能成功跨 Apartment 界限。</span><span class="sxs-lookup"><span data-stu-id="1fa12-183">You must register the type library of the COM component for calls to successfully cross the apartment boundary.</span></span>  
  
-   <span data-ttu-id="1fa12-184">將用戶端執行緒設定為 STA 或 MTA 來變更主執行緒。</span><span class="sxs-lookup"><span data-stu-id="1fa12-184">Alter the main thread by setting the client thread to STA or MTA.</span></span> <span data-ttu-id="1fa12-185">例如，如果您的 C# 用戶端呼叫許多 STA COM 元件，您可以將主執行緒設定為 STA，以避免跨 Apartment 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-185">For example, if your C# client calls many STA COM components, you can avoid cross-apartment marshaling by setting the main thread to STA.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1fa12-186">將 C# 用戶端的執行緒設定為 STA 之後，對 MTA COM 元件的呼叫會需要跨 Apartment 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-186">Once the thread of a C# client is set to STA, calls to MTA COM components will require cross-apartment marshaling.</span></span>  
  
 <span data-ttu-id="1fa12-187">如需明確選取 Apartment 模型的指示，請參閱 [Managed 和 Unmanaged 執行緒處理](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-187">For instructions on explicitly selecting an apartment model, see [Managed and Unmanaged Threading](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5).</span></span>  
  
 [<span data-ttu-id="1fa12-188">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1fa12-188">Back to top</span></span>](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a><span data-ttu-id="1fa12-189">封送處理遠端呼叫</span><span class="sxs-lookup"><span data-stu-id="1fa12-189">Marshaling Remote Calls</span></span>  
 <span data-ttu-id="1fa12-190">如同跨 Apartment 封送處理，當物件位於不同的處理序時，在 Managed 和 Unmanaged 程式碼之間的每一個呼叫都需要 COM 封送處理。</span><span class="sxs-lookup"><span data-stu-id="1fa12-190">As with cross-apartment marshaling, COM marshaling is involved in each call between managed and unmanaged code whenever the objects reside in separate processes.</span></span> <span data-ttu-id="1fa12-191">例如：</span><span class="sxs-lookup"><span data-stu-id="1fa12-191">For example:</span></span>  
  
-   <span data-ttu-id="1fa12-192">在遠端主機上叫用 Managed 伺服器的 COM 用戶端會使用分散式 COM (DCOM)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-192">A COM client that invokes a managed server on a remote host uses distributed COM (DCOM).</span></span>  
  
-   <span data-ttu-id="1fa12-193">在遠端主機上叫用 COM 伺服器的 Managed 用戶端會使用 DCOM。</span><span class="sxs-lookup"><span data-stu-id="1fa12-193">A managed client that invokes a COM server on a remote host uses DCOM.</span></span>  
  
 <span data-ttu-id="1fa12-194">下圖顯示 Interop 封送處理和 COM 封送處理如何跨處理序和主機界限提供通訊通道。</span><span class="sxs-lookup"><span data-stu-id="1fa12-194">The following illustration shows how interop marshaling and COM marshaling provide communications channels across process and host boundaries.</span></span>  
  
 <span data-ttu-id="1fa12-195">![COM 封送處理](../../../docs/framework/interop/media/interophost.gif "interophost")</span><span class="sxs-lookup"><span data-stu-id="1fa12-195">![COM marshaling](../../../docs/framework/interop/media/interophost.gif "interophost")</span></span>  
<span data-ttu-id="1fa12-196">跨處理序封送處理</span><span class="sxs-lookup"><span data-stu-id="1fa12-196">Cross-process marshaling</span></span>  
  
### <a name="preserving-identity"></a><span data-ttu-id="1fa12-197">保留識別</span><span class="sxs-lookup"><span data-stu-id="1fa12-197">Preserving Identity</span></span>  
 <span data-ttu-id="1fa12-198">Common Language Runtime 會保留 Managed 和 Unmanaged 參考的識別。</span><span class="sxs-lookup"><span data-stu-id="1fa12-198">The common language runtime preserves the identity of managed and unmanaged references.</span></span> <span data-ttu-id="1fa12-199">下圖顯示跨處理序和主機界限的直接 Unmanaged 參考 (上方列) 和直接 Managed 參考 (下方列) 的流程。</span><span class="sxs-lookup"><span data-stu-id="1fa12-199">The following illustration shows the flow of direct unmanaged references (top row) and direct managed references (bottom row) across process and host boundaries.</span></span>  
  
 <span data-ttu-id="1fa12-200">![COM 可呼叫包裝函式和執行階段可呼叫包裝函式](../../../docs/framework/interop/media/interopdirectref.gif "interopdirectref")</span><span class="sxs-lookup"><span data-stu-id="1fa12-200">![COM callable wrapper and runtime callable wrapper](../../../docs/framework/interop/media/interopdirectref.gif "interopdirectref")</span></span>  
<span data-ttu-id="1fa12-201">跨處理序和主機界限傳遞的參考</span><span class="sxs-lookup"><span data-stu-id="1fa12-201">Reference passing across process and host boundaries</span></span>  
  
 <span data-ttu-id="1fa12-202">在本圖中：</span><span class="sxs-lookup"><span data-stu-id="1fa12-202">In this illustration:</span></span>  
  
-   <span data-ttu-id="1fa12-203">Unmanaged 用戶端會從 Managed 物件取得 COM 物件的參考 (Managed 物件會從遠端主機取得這個參考)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-203">An unmanaged client gets a reference to a COM object from a managed object that gets this reference from a remote host.</span></span> <span data-ttu-id="1fa12-204">遠端處理機制是 DCOM。</span><span class="sxs-lookup"><span data-stu-id="1fa12-204">The remoting mechanism is DCOM.</span></span>  
  
-   <span data-ttu-id="1fa12-205">Managed 用戶端會從 COM 物件取得 Managed 物件的參考 (COM 物件會從遠端主機取得這個參考)。</span><span class="sxs-lookup"><span data-stu-id="1fa12-205">A managed client gets a reference to a managed object from a COM object that gets this reference from a remote host.</span></span> <span data-ttu-id="1fa12-206">遠端處理機制是 DCOM。</span><span class="sxs-lookup"><span data-stu-id="1fa12-206">The remoting mechanism is DCOM.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1fa12-207">必須註冊 Managed 伺服器的匯出類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="1fa12-207">The exported type library of the managed server must be registered.</span></span>  
  
 <span data-ttu-id="1fa12-208">呼叫端和被呼叫端之間的處理序界限數目並不相關；同處理序和跨處理序呼叫會有相同的直接參考。</span><span class="sxs-lookup"><span data-stu-id="1fa12-208">The number of process boundaries between caller and callee is irrelevant; the same direct referencing occurs for in-process and out-of-process calls.</span></span>  
  
### <a name="managed-remoting"></a><span data-ttu-id="1fa12-209">Managed 遠端處理</span><span class="sxs-lookup"><span data-stu-id="1fa12-209">Managed Remoting</span></span>  
 <span data-ttu-id="1fa12-210">執行階段也會提供 Managed 遠端處理，可供您用來建立跨處理序和主機界限的 Managed 物件之間的通訊通道。</span><span class="sxs-lookup"><span data-stu-id="1fa12-210">The runtime also provides managed remoting, which you can use to establish a communications channel between managed objects across process and host boundaries.</span></span> <span data-ttu-id="1fa12-211">Managed 遠端處理可以提供通訊元件之間的防火牆，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1fa12-211">Managed remoting can accommodate a firewall between the communicating components, as the following illustration shows.</span></span>  
  
 <span data-ttu-id="1fa12-212">![SOAP 或 TcpChannel](../../../docs/framework/interop/media/interopremotesoap.gif "interopremotesoap")</span><span class="sxs-lookup"><span data-stu-id="1fa12-212">![SOAP or TcpChannel](../../../docs/framework/interop/media/interopremotesoap.gif "interopremotesoap")</span></span>  
<span data-ttu-id="1fa12-213">使用 SOAP 或 TcpChannel 類別跨防火牆進行遠端呼叫</span><span class="sxs-lookup"><span data-stu-id="1fa12-213">Remote calls across firewalls using SOAP or the TcpChannel class</span></span>  
  
 <span data-ttu-id="1fa12-214">某些 Unmanaged 呼叫可以透過 SOAP 進行傳送，例如 [Serviced 元件](http://msdn.microsoft.com/en-us/f109ee24-81ad-4d99-9892-51ac6f34978c)和 COM 之間的呼叫。</span><span class="sxs-lookup"><span data-stu-id="1fa12-214">Some unmanaged calls can be channeled through SOAP, such as the calls between [serviced components](http://msdn.microsoft.com/en-us/f109ee24-81ad-4d99-9892-51ac6f34978c) and COM.</span></span>  
  
 [<span data-ttu-id="1fa12-215">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1fa12-215">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="1fa12-216">相關主題</span><span class="sxs-lookup"><span data-stu-id="1fa12-216">Related Topics</span></span>  
  
|<span data-ttu-id="1fa12-217">標題</span><span class="sxs-lookup"><span data-stu-id="1fa12-217">Title</span></span>|<span data-ttu-id="1fa12-218">說明</span><span class="sxs-lookup"><span data-stu-id="1fa12-218">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1fa12-219">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="1fa12-219">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)|<span data-ttu-id="1fa12-220">描述 Interop 封送處理服務用來封送處理資料的規則。</span><span class="sxs-lookup"><span data-stu-id="1fa12-220">Describes the rules that the interop marshaling service uses to marshal data.</span></span>|  
|[<span data-ttu-id="1fa12-221">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="1fa12-221">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)|<span data-ttu-id="1fa12-222">描述如何宣告方法參數，以及將引數傳遞給 Unmanaged 程式庫所匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="1fa12-222">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>|  
|[<span data-ttu-id="1fa12-223">使用 COM Interop 封送處理資料</span><span class="sxs-lookup"><span data-stu-id="1fa12-223">Marshaling Data with COM Interop</span></span>](../../../docs/framework/interop/marshaling-data-with-com-interop.md)|<span data-ttu-id="1fa12-224">描述如何自訂 COM 包裝函式來變更封送處理行為。</span><span class="sxs-lookup"><span data-stu-id="1fa12-224">Describes how to customize COM wrappers to alter marshaling behavior.</span></span>|  
|[<span data-ttu-id="1fa12-225">如何：將 Managed 程式碼 DCOM 移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="1fa12-225">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)|<span data-ttu-id="1fa12-226">描述如何從 DCOM 移轉至 WCF。</span><span class="sxs-lookup"><span data-stu-id="1fa12-226">Describes how to migrate from DCOM to WCF.</span></span>|  
|[<span data-ttu-id="1fa12-227">操作說明：對應 HRESULT 和例外狀況</span><span class="sxs-lookup"><span data-stu-id="1fa12-227">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)|<span data-ttu-id="1fa12-228">描述如何將自訂例外狀況對應到 HRESULT，並提供每一個 HRESULT 與其在 .NET Framework 中可比較的例外狀況類別之完整對應。</span><span class="sxs-lookup"><span data-stu-id="1fa12-228">Describes how to map custom exceptions to HRESULTs and provides the complete mapping from each HRESULT to its comparable exception class in the .NET Framework.</span></span>|  
|[<span data-ttu-id="1fa12-229">使用泛型型別互通</span><span class="sxs-lookup"><span data-stu-id="1fa12-229">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)|<span data-ttu-id="1fa12-230">描述使用泛型類型來取得 COM 互通性時所支援的動作。</span><span class="sxs-lookup"><span data-stu-id="1fa12-230">Describes which actions are supported when using generic types for COM interoperability.</span></span>|  
|[<span data-ttu-id="1fa12-231">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="1fa12-231">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)|<span data-ttu-id="1fa12-232">描述 Common Language Runtime 提供的互通性服務。</span><span class="sxs-lookup"><span data-stu-id="1fa12-232">Describes interoperability services provided by the common language runtime.</span></span>|  
|[<span data-ttu-id="1fa12-233">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="1fa12-233">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|<span data-ttu-id="1fa12-234">提供有關將 COM 元件納入 .NET Framework 應用程式的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="1fa12-234">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>|  
|[<span data-ttu-id="1fa12-235">交互操作的設計考量</span><span class="sxs-lookup"><span data-stu-id="1fa12-235">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)|<span data-ttu-id="1fa12-236">提供撰寫整合式 COM 元件的秘訣。</span><span class="sxs-lookup"><span data-stu-id="1fa12-236">Provides tips for writing integrated COM components.</span></span>|  
  
 [<span data-ttu-id="1fa12-237">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1fa12-237">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="1fa12-238">參考資料</span><span class="sxs-lookup"><span data-stu-id="1fa12-238">Reference</span></span>  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [<span data-ttu-id="1fa12-239">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1fa12-239">Back to top</span></span>](#top)
