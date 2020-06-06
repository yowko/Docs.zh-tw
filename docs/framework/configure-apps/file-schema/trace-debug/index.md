---
title: 追蹤和偵錯設定結構描述
ms.date: 03/30/2017
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
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927125"
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="53aea-102">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="53aea-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="53aea-103">追蹤和偵錯設定會指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="53aea-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="53aea-104">下表描述每個追蹤和偵錯設定項目的函式。</span><span class="sxs-lookup"><span data-stu-id="53aea-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="53aea-105">元素</span><span class="sxs-lookup"><span data-stu-id="53aea-105">Element</span></span>|<span data-ttu-id="53aea-106">描述</span><span class="sxs-lookup"><span data-stu-id="53aea-106">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="53aea-107">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="53aea-107">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="53aea-108">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="53aea-108">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<add>](add-element-for-sharedlisteners.md)|<span data-ttu-id="53aea-109">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="53aea-109">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="53aea-110">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="53aea-110">Specifies the level where a trace switch is set.</span></span>|  
|[\<assert>](assert-element.md)|<span data-ttu-id="53aea-111">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="53aea-111">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="53aea-112">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="53aea-112">Clears the `Listeners` collection for a trace source.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="53aea-113">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="53aea-113">Clears the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="53aea-114">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-114">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="53aea-115">將篩選新增至追蹤之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-115">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="53aea-116">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-116">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="53aea-117">為追蹤來源的 `Listeners` 集合指定接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-117">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="53aea-118">為追蹤的 `Listeners` 集合指定接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-118">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="53aea-119">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="53aea-119">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="53aea-120">從追蹤的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-120">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="53aea-121">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-121">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="53aea-122">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-122">Contains listeners that any source or trace element can reference.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="53aea-123">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="53aea-123">Contains trace sources that initiate tracing messages.</span></span>|  
|[\<source>](source-element.md)|<span data-ttu-id="53aea-124">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="53aea-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="53aea-125">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="53aea-125">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[\<system.diagnostics>](system-diagnostics-element.md)|<span data-ttu-id="53aea-126">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="53aea-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="53aea-127">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="53aea-127">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53aea-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53aea-128">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="53aea-129">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="53aea-129">Configuration File Schema</span></span>](../index.md)
