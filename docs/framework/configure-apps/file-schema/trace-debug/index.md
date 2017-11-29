---
title: "追蹤和偵錯設定結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 97c96fbb1abf969d902159709ca0e738f475fab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="49bd0-102">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="49bd0-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="49bd0-103">追蹤和偵錯設定會指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="49bd0-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="49bd0-104">下表描述每個追蹤和偵錯設定項目的函式。</span><span class="sxs-lookup"><span data-stu-id="49bd0-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="49bd0-105">項目</span><span class="sxs-lookup"><span data-stu-id="49bd0-105">Element</span></span>|<span data-ttu-id="49bd0-106">描述</span><span class="sxs-lookup"><span data-stu-id="49bd0-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49bd0-107">\<add></span><span class="sxs-lookup"><span data-stu-id="49bd0-107">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="49bd0-108">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="49bd0-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="49bd0-109">\<add></span><span class="sxs-lookup"><span data-stu-id="49bd0-109">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="49bd0-110">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="49bd0-110">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="49bd0-111">\<add></span><span class="sxs-lookup"><span data-stu-id="49bd0-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|<span data-ttu-id="49bd0-112">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="49bd0-112">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="49bd0-113">\<add></span><span class="sxs-lookup"><span data-stu-id="49bd0-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="49bd0-114">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="49bd0-114">Specifies the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="49bd0-115">\<assert></span><span class="sxs-lookup"><span data-stu-id="49bd0-115">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="49bd0-116">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="49bd0-116">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="49bd0-117">\<clear></span><span class="sxs-lookup"><span data-stu-id="49bd0-117">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="49bd0-118">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="49bd0-118">Clears the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="49bd0-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="49bd0-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="49bd0-120">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="49bd0-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="49bd0-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="49bd0-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="49bd0-122">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-122">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="49bd0-123">\<filter></span><span class="sxs-lookup"><span data-stu-id="49bd0-123">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="49bd0-124">將篩選新增至追蹤之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-124">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="49bd0-125">\<filter></span><span class="sxs-lookup"><span data-stu-id="49bd0-125">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="49bd0-126">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-126">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="49bd0-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="49bd0-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="49bd0-128">為追蹤來源的 `Listeners` 集合指定接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-128">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="49bd0-129">\<listeners></span><span class="sxs-lookup"><span data-stu-id="49bd0-129">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="49bd0-130">為追蹤的 `Listeners` 集合指定接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-130">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="49bd0-131">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="49bd0-131">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="49bd0-132">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="49bd0-132">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="49bd0-133">\<remove></span><span class="sxs-lookup"><span data-stu-id="49bd0-133">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="49bd0-134">從追蹤的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-134">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="49bd0-135">\<remove></span><span class="sxs-lookup"><span data-stu-id="49bd0-135">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="49bd0-136">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-136">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="49bd0-137">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="49bd0-137">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="49bd0-138">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-138">Contains listeners that any source or trace element can reference.</span></span>|  
|[<span data-ttu-id="49bd0-139">\<sources></span><span class="sxs-lookup"><span data-stu-id="49bd0-139">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="49bd0-140">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="49bd0-140">Contains trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="49bd0-141">\<source></span><span class="sxs-lookup"><span data-stu-id="49bd0-141">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="49bd0-142">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="49bd0-142">Specifies a trace source that initiates tracing messages.</span></span>|  
|[<span data-ttu-id="49bd0-143">\<switches></span><span class="sxs-lookup"><span data-stu-id="49bd0-143">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="49bd0-144">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="49bd0-144">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[<span data-ttu-id="49bd0-145">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="49bd0-145">\<system.diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|<span data-ttu-id="49bd0-146">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="49bd0-146">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="49bd0-147">\<trace></span><span class="sxs-lookup"><span data-stu-id="49bd0-147">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="49bd0-148">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="49bd0-148">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49bd0-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49bd0-149">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="49bd0-150">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="49bd0-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
