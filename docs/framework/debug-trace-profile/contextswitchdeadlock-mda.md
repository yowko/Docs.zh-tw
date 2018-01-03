---
title: contextSwitchDeadlock MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 816afbae0cca18de24c11152541a509b54c119b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="ab75b-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="ab75b-102">contextSwitchDeadlock MDA</span></span>
<span data-ttu-id="ab75b-103">試圖進行 COM 內容轉換期間，偵測到死結時，會啟用 `contextSwitchDeadlock` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="ab75b-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ab75b-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="ab75b-104">Symptoms</span></span>  
 <span data-ttu-id="ab75b-105">最常見的徵兆是，在 Unmanaged COM 元件上從 Managed 程式碼進行的呼叫未傳回。</span><span class="sxs-lookup"><span data-stu-id="ab75b-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="ab75b-106">另一個徵兆是記憶體使用量隨著時間增加。</span><span class="sxs-lookup"><span data-stu-id="ab75b-106">Another symptom is memory usage increasing over time.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ab75b-107">原因</span><span class="sxs-lookup"><span data-stu-id="ab75b-107">Cause</span></span>  
 <span data-ttu-id="ab75b-108">最有可能的原因是，單一執行緒 Apartment (STA) 執行緒沒有提取訊息。</span><span class="sxs-lookup"><span data-stu-id="ab75b-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="ab75b-109">STA 執行緒可能正在等待而沒有提取訊息，或是正在執行長時間作業，不允許訊息佇列提取。</span><span class="sxs-lookup"><span data-stu-id="ab75b-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>  
  
 <span data-ttu-id="ab75b-110">記憶體使用量隨著時間增加的原因，是因為完成項執行緒試圖在 Unmanaged COM 元件上呼叫 `Release`，而該元件未傳回。</span><span class="sxs-lookup"><span data-stu-id="ab75b-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="ab75b-111">這會導致完成項無法回收其他物件。</span><span class="sxs-lookup"><span data-stu-id="ab75b-111">This prevents the finalizer from reclaiming other objects.</span></span>  
  
 <span data-ttu-id="ab75b-112">根據預設，Visual Basic 主控台應用程式主要執行緒的執行緒模型為 STA。</span><span class="sxs-lookup"><span data-stu-id="ab75b-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="ab75b-113">如果 STA 執行緒直接或間接透過通用語言執行平台或協力廠商控制項來使用 COM 互通性，就會啟用此 MDA。</span><span class="sxs-lookup"><span data-stu-id="ab75b-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="ab75b-114">若要避免在 Visual Basic 主控台應用程式中啟用此 MDA，請將 <xref:System.MTAThreadAttribute> 屬性套用至 Main 方法，或修改應用程式來提取訊問。</span><span class="sxs-lookup"><span data-stu-id="ab75b-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>  
  
 <span data-ttu-id="ab75b-115">在符合下列所有條件的情況下，有可能會錯誤地啟用此 MDA：</span><span class="sxs-lookup"><span data-stu-id="ab75b-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="ab75b-116">應用程式直接或間接透過程式庫，從 STA 執行緒建立 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="ab75b-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>  
  
-   <span data-ttu-id="ab75b-117">已在偵錯工具中停止應用程式，而使用者繼續應用程式，或執行步驟作業。</span><span class="sxs-lookup"><span data-stu-id="ab75b-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>  
  
-   <span data-ttu-id="ab75b-118">未啟用 Unmanaged 偵錯。</span><span class="sxs-lookup"><span data-stu-id="ab75b-118">Unmanaged debugging is not enabled.</span></span>  
  
 <span data-ttu-id="ab75b-119">若要判斷是否錯誤地啟用 MDA，請停用所有中斷點、重新啟動應用程式，並且讓它不間斷地執行。</span><span class="sxs-lookup"><span data-stu-id="ab75b-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="ab75b-120">如果未啟用 MDA，則可能初始啟用時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab75b-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="ab75b-121">若是如此，請停用 MDA，以避免阻礙偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="ab75b-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab75b-122">此 MDA 在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 及較新版本的預設集中。</span><span class="sxs-lookup"><span data-stu-id="ab75b-122">This MDA is in the default set for [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and later versions.</span></span> <span data-ttu-id="ab75b-123">當 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中啟用裝載處理序時，您無法停用預設集中的 MDA。</span><span class="sxs-lookup"><span data-stu-id="ab75b-123">When the hosting process is enabled in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], you cannot disable MDAs that are in the default set.</span></span> <span data-ttu-id="ab75b-124">預設會啟用裝載處理序，所以必須明確將其停用。</span><span class="sxs-lookup"><span data-stu-id="ab75b-124">The hosting process is enabled by default, so it must be explicitly disabled.</span></span> <span data-ttu-id="ab75b-125">如需如何停用 MDA 的資訊，請參閱[診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)中的＜啟用和停用 MDA＞。</span><span class="sxs-lookup"><span data-stu-id="ab75b-125">For information about how to disable MDAs, see "Enabling and Disabling MDAs" in [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ab75b-126">解決方式</span><span class="sxs-lookup"><span data-stu-id="ab75b-126">Resolution</span></span>  
 <span data-ttu-id="ab75b-127">遵循有關 STA 訊息幫浦的 COM 規則。</span><span class="sxs-lookup"><span data-stu-id="ab75b-127">Follow COM rules regarding STA message pumping.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ab75b-128">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="ab75b-128">Effect on the Runtime</span></span>  
 <span data-ttu-id="ab75b-129">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="ab75b-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ab75b-130">它只會提報 COM 內容的相關資料。</span><span class="sxs-lookup"><span data-stu-id="ab75b-130">It only reports data about COM contexts.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ab75b-131">輸出</span><span class="sxs-lookup"><span data-stu-id="ab75b-131">Output</span></span>  
 <span data-ttu-id="ab75b-132">描述目前內容和目標內容的訊息。</span><span class="sxs-lookup"><span data-stu-id="ab75b-132">A message describing the current context and the target context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ab75b-133">組態</span><span class="sxs-lookup"><span data-stu-id="ab75b-133">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab75b-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab75b-134">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="ab75b-135">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="ab75b-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="ab75b-136">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="ab75b-136">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
