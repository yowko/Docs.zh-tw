---
title: "動態地啟用分析的追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d86186d3f979d4ec02cb728befb7127edfd07aaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dynamically-enabling-analytic-tracing"></a><span data-ttu-id="d4afb-102">動態地啟用分析的追蹤</span><span class="sxs-lookup"><span data-stu-id="d4afb-102">Dynamically Enabling Analytic Tracing</span></span>
<span data-ttu-id="d4afb-103">使用隨附於 Windows 作業系統的工具，您可以使用 Windows 事件追蹤 (ETW) 來動態啟用或停用追蹤。</span><span class="sxs-lookup"><span data-stu-id="d4afb-103">Using tools that ship with the Windows operating system, you can enable or disable tracing dynamically using Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="d4afb-104">對所有的 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務而言，分析追蹤可以不需要以修改應用程式的 Web.config 檔案或重新啟動服務的方式，來動態啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="d4afb-104">For all [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, analytic tracing can be enabled and disabled dynamically without modifying the application’s Web.config file or restarting the service.</span></span> <span data-ttu-id="d4afb-105">這樣可讓發出追蹤事件的應用程式維持不變。</span><span class="sxs-lookup"><span data-stu-id="d4afb-105">This allows the application that emits the trace events to remain undisturbed.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="d4afb-106"> 追蹤選項可以使用類似的方法來設定。</span><span class="sxs-lookup"><span data-stu-id="d4afb-106"> tracing options can be configured in a similar way.</span></span> <span data-ttu-id="d4afb-107">例如，您可以將嚴重性層級從 **Error** 變更為 **Information** ，無須干擾應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4afb-107">For example, you can change the severity level from **Error** to **Information** without disturbing the application.</span></span> <span data-ttu-id="d4afb-108">使用下列工具即可達到這個目的：</span><span class="sxs-lookup"><span data-stu-id="d4afb-108">This can be done using the following tools:</span></span>  
  
-   <span data-ttu-id="d4afb-109">**Logman** – 命令列工具，用來設定、控制和查詢追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="d4afb-109">**Logman** – A command line tool for configuring, controlling, and querying tracing data.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="d4afb-110">[Logman 建立追蹤](http://go.microsoft.com/fwlink/?LinkId=165426)和[Logman 更新追蹤](http://go.microsoft.com/fwlink/?LinkId=165427)。</span><span class="sxs-lookup"><span data-stu-id="d4afb-110"> [Logman Create Trace](http://go.microsoft.com/fwlink/?LinkId=165426) and [Logman Update Trace](http://go.microsoft.com/fwlink/?LinkId=165427).</span></span>  
  
-   <span data-ttu-id="d4afb-111">**EventViewer** - Windows 圖形管理工具，用來檢視追蹤結果。</span><span class="sxs-lookup"><span data-stu-id="d4afb-111">**EventViewer** - Windows graphical management tool for viewing the results of tracing.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="d4afb-112">[WCF 服務和 Windows 事件追蹤](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)和[事件檢視器](http://go.microsoft.com/fwlink/?LinkId=165428)。</span><span class="sxs-lookup"><span data-stu-id="d4afb-112"> [WCF Services and Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) and [Event Viewer](http://go.microsoft.com/fwlink/?LinkId=165428).</span></span>  
  
-   <span data-ttu-id="d4afb-113">**Perfmon** – Windows 圖形管理工具，使用計數器來監事追蹤計數器和對於效能的追蹤效果。</span><span class="sxs-lookup"><span data-stu-id="d4afb-113">**Perfmon** – Windows graphical management tool that uses counters to monitor tracing counters and the effects of tracing on performance.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="d4afb-114">[手動建立資料收集器集合工具](http://go.microsoft.com/fwlink/?LinkId=165429)。</span><span class="sxs-lookup"><span data-stu-id="d4afb-114"> [Create a Data Collector Set Manually](http://go.microsoft.com/fwlink/?LinkId=165429).</span></span>  
  
### <a name="keywords"></a><span data-ttu-id="d4afb-115">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d4afb-115">Keywords</span></span>  
 <span data-ttu-id="d4afb-116">使用 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> 類別時，.NET Framework 追蹤訊息一般會由嚴重性層級加以篩選 (例如，[錯誤]、[警告] 和 [資訊])。</span><span class="sxs-lookup"><span data-stu-id="d4afb-116">When using the <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> class, .NET Framework trace messages are generally filtered by the severity level (for example, Error, Warning, and Information).</span></span> <span data-ttu-id="d4afb-117">ETW 支援嚴重性層級的概念，不過會使用關鍵字引入全新、有彈性的篩選機制。</span><span class="sxs-lookup"><span data-stu-id="d4afb-117">ETW supports the severity level concept, but introduces a new, flexible filter mechanism using keywords.</span></span> <span data-ttu-id="d4afb-118">關鍵字是任意的文字值，可讓追蹤事件提供額外的內容，說明該事件的意義。</span><span class="sxs-lookup"><span data-stu-id="d4afb-118">Keywords are arbitrary textual values that let tracing events provide additional context about what that event means.</span></span>  
  
 <span data-ttu-id="d4afb-119">若是 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤，每個追蹤事件都有兩種類型的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d4afb-119">For [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing, each trace event has two types of keywords.</span></span> <span data-ttu-id="d4afb-120">第一，每個事件會有一個或多個案例關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d4afb-120">First, each event has one or more scenario keywords.</span></span> <span data-ttu-id="d4afb-121">這些關鍵字會向案例表示，此事件提供支援。</span><span class="sxs-lookup"><span data-stu-id="d4afb-121">These keywords denote the scenarios that this event is intended to support.</span></span> <span data-ttu-id="d4afb-122">有三組案例關鍵字，每組都是為特定目的而設計，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="d4afb-122">There are three scenario keywords, each designed for a specific purpose as shown in the following table.</span></span> <span data-ttu-id="d4afb-123">使用關鍵字篩選可以不需要干擾 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務來動態變更。</span><span class="sxs-lookup"><span data-stu-id="d4afb-123">Filtering using keywords can be changed dynamically without disturbing the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="d4afb-124">這代表您可以動態變更目前的追蹤案例和蒐集的追蹤資訊數量。</span><span class="sxs-lookup"><span data-stu-id="d4afb-124">That means that you can dynamically change your current tracing scenario and the amount of tracing information you gather.</span></span> <span data-ttu-id="d4afb-125">例如，您可以將 `HealthMonitoring` 變更為 `Troubleshooting` 並增加追蹤事件細微性。</span><span class="sxs-lookup"><span data-stu-id="d4afb-125">For example, you can change `HealthMonitoring` to `Troubleshooting` and increase Tracing Event granularity.</span></span>  
  
|<span data-ttu-id="d4afb-126">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d4afb-126">Keyword</span></span>|<span data-ttu-id="d4afb-127">描述</span><span class="sxs-lookup"><span data-stu-id="d4afb-127">Description</span></span>|  
|-------------|-----------------|  
|`HealthMonitoring`|<span data-ttu-id="d4afb-128">非常輕微、有限度的追蹤，讓您監視服務的活動。</span><span class="sxs-lookup"><span data-stu-id="d4afb-128">Very lightweight, minimal tracing that lets you monitor your service’s activity.</span></span>|  
|`EndToEndMonitoring`|<span data-ttu-id="d4afb-129">用來支援訊息流動追蹤的事件。</span><span class="sxs-lookup"><span data-stu-id="d4afb-129">Events used to support message flow tracing.</span></span>|  
|`Troubleshooting`|<span data-ttu-id="d4afb-130">更多細微性事件圍繞 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]的擴充性點。</span><span class="sxs-lookup"><span data-stu-id="d4afb-130">More granular events around the extensibility points of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>|  
  
 <span data-ttu-id="d4afb-131">第二組關鍵字會定義哪個 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 元件發出事件。</span><span class="sxs-lookup"><span data-stu-id="d4afb-131">The second group of keywords define which component of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitted the event.</span></span>  
  
|<span data-ttu-id="d4afb-132">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d4afb-132">Keyword</span></span>|<span data-ttu-id="d4afb-133">描述</span><span class="sxs-lookup"><span data-stu-id="d4afb-133">Description</span></span>|  
|-------------|-----------------|  
|`UserEvents`|<span data-ttu-id="d4afb-134">由使用者程式碼而不是 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="d4afb-134">Events emitted by the user code and not the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span>|  
|`ServiceModel`|<span data-ttu-id="d4afb-135">由 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 執行階段所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="d4afb-135">Events emitted by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] runtime.</span></span>|  
|`ServiceHost`|<span data-ttu-id="d4afb-136">由服務主機所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="d4afb-136">Events emitted by the service host.</span></span>|  
|`WCFMessageLogging`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="d4afb-137"> 訊息記錄事件。</span><span class="sxs-lookup"><span data-stu-id="d4afb-137"> message logging events.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4afb-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4afb-138">See Also</span></span>  
 [<span data-ttu-id="d4afb-139">WCF Services and Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="d4afb-139">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
