---
title: "用戶端的 UI 自動化事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
caps.latest.revision: "32"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8486f8c8eaa586f6f81ea895fd22c96801b3594b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ui-automation-events-for-clients"></a><span data-ttu-id="4e3d7-102">用戶端的 UI 自動化事件</span><span class="sxs-lookup"><span data-stu-id="4e3d7-102">UI Automation Events for Clients</span></span>
> [!NOTE]
>  <span data-ttu-id="4e3d7-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4e3d7-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4e3d7-105">本主題描述如何[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]事件由使用者介面自動化用戶端。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-105">This topic describes how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] events are used by UI Automation clients.</span></span>  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="4e3d7-106">允許用戶端訂閱感興趣的事件。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-106"> allows clients to subscribe to events of interest.</span></span> <span data-ttu-id="4e3d7-107">這項功能會提高效能而不必持續輪詢所有[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]系統上，以查看是否有變更任何資訊、 結構或狀態中的項目。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-107">This capability improves performance by eliminating the need to continually poll all the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements in the system to see if any information, structure, or state has changed.</span></span>  
  
 <span data-ttu-id="4e3d7-108">同時也因為能夠只接聽定義範圍內的事件，而改善效率。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-108">Efficiency is also improved by the ability to listen for events only within a defined scope.</span></span> <span data-ttu-id="4e3d7-109">例如，用戶端可以接聽的焦點變更事件上所有[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目在樹狀目錄中，或只有一個項目和其下階。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-109">For example, a client can listen for focus change events on all [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements in the tree, or on just one element and its descendants.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e3d7-110">不會假設所有可能的事件，會引發由[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]提供者。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-110">Do not assume that all possible events are raised by a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] provider.</span></span> <span data-ttu-id="4e3d7-111">例如，並非所有的屬性變更都會導致標準 proxy 提供者所引發的事件[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]和[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-111">For example, not all property changes cause events to be raised by the standard proxy providers for [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls.</span></span>  
  
 <span data-ttu-id="4e3d7-112">如需更廣泛的檢視[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]事件，請參閱[UI 自動化事件概觀](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-112">For a broader view of [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] events, see [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).</span></span>  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a><span data-ttu-id="4e3d7-113">訂閱事件</span><span class="sxs-lookup"><span data-stu-id="4e3d7-113">Subscribing to Events</span></span>  
 <span data-ttu-id="4e3d7-114">用戶端應用程式藉由使用下列方法之一註冊事件處理常式，來訂閱特定種類的事件。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-114">Client applications subscribe to events of a particular kind by registering an event handler, using one of the following methods.</span></span>  
  
|<span data-ttu-id="4e3d7-115">方法</span><span class="sxs-lookup"><span data-stu-id="4e3d7-115">Method</span></span>|<span data-ttu-id="4e3d7-116">事件類型</span><span class="sxs-lookup"><span data-stu-id="4e3d7-116">Event Type</span></span>|<span data-ttu-id="4e3d7-117">事件引數類型</span><span class="sxs-lookup"><span data-stu-id="4e3d7-117">Event Arguments Type</span></span>|<span data-ttu-id="4e3d7-118">委派類型</span><span class="sxs-lookup"><span data-stu-id="4e3d7-118">Delegate Type</span></span>|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|<span data-ttu-id="4e3d7-119">焦點變更</span><span class="sxs-lookup"><span data-stu-id="4e3d7-119">Focus change</span></span>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|<span data-ttu-id="4e3d7-120">屬性變更</span><span class="sxs-lookup"><span data-stu-id="4e3d7-120">Property change</span></span>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|<span data-ttu-id="4e3d7-121">結構變更</span><span class="sxs-lookup"><span data-stu-id="4e3d7-121">Structure change</span></span>|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|<span data-ttu-id="4e3d7-122">所有其他事件，由<xref:System.Windows.Automation.AutomationEvent></span><span class="sxs-lookup"><span data-stu-id="4e3d7-122">All other events, identified by an <xref:System.Windows.Automation.AutomationEvent></span></span>|<span data-ttu-id="4e3d7-123"><xref:System.Windows.Automation.AutomationEventArgs> 或 <xref:System.Windows.Automation.WindowClosedEventArgs></span><span class="sxs-lookup"><span data-stu-id="4e3d7-123"><xref:System.Windows.Automation.AutomationEventArgs> or <xref:System.Windows.Automation.WindowClosedEventArgs></span></span>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 <span data-ttu-id="4e3d7-124">在呼叫方法之前，您必須建立委派方法來處理事件。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-124">Before calling the method, you must create a delegate method to handle the event.</span></span> <span data-ttu-id="4e3d7-125">您想要的話也可以在單一方法中處理不同類型的事件，並在對資料中其一個方法的多次呼叫裡傳遞此方法。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-125">If you prefer, you can handle different kinds of events in a single method, and pass this method in multiple calls to one of the methods in the table.</span></span> <span data-ttu-id="4e3d7-126">例如，單一<xref:System.Windows.Automation.AutomationEventHandler>可以設定以處理各種事件以不同的方式根據<xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-126">For example, a single <xref:System.Windows.Automation.AutomationEventHandler> can be set up to handle various events differently according to the <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e3d7-127">若要處理視窗關閉事件，轉型會傳遞至事件處理常式的引數類型<xref:System.Windows.Automation.WindowClosedEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-127">To process window-closed events, cast the argument type that is passed to the event handler as <xref:System.Windows.Automation.WindowClosedEventArgs>.</span></span> <span data-ttu-id="4e3d7-128">因為[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]視窗項目已不再有效，您無法使用`sender`參數來擷取資訊; 使用<xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A>改為。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-128">Because the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] element for the window is no longer valid, you cannot use the `sender` parameter to retrieve information; use <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> instead.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4e3d7-129">如果您的應用程式可能會收到事件從自己的[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]，請勿使用您的應用程式[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]執行緒來訂閱事件，或取消訂閱。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-129">If your application might receive events from its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], do not use your application's [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread to subscribe to events, or to unsubscribe.</span></span> <span data-ttu-id="4e3d7-130">這樣可能會導致無法預期的行為。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-130">Doing so might lead to unpredictable behavior.</span></span> <span data-ttu-id="4e3d7-131">如需詳細資訊，請參閱 [UI Automation Threading Issues](../../../docs/framework/ui-automation/ui-automation-threading-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-131">For more information, see [UI Automation Threading Issues](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).</span></span>  
  
 <span data-ttu-id="4e3d7-132">在關閉，或當[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]事件不會再感興趣的應用程式、 使用者介面自動化用戶端應該呼叫下列方法之一。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-132">On shutdown, or when [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] events are no longer of interest to the application, UI Automation clients should call one of the following methods.</span></span>  
  
|<span data-ttu-id="4e3d7-133">方法</span><span class="sxs-lookup"><span data-stu-id="4e3d7-133">Method</span></span>|<span data-ttu-id="4e3d7-134">描述</span><span class="sxs-lookup"><span data-stu-id="4e3d7-134">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|<span data-ttu-id="4e3d7-135">移除註冊使用已註冊的事件處理常式<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-135">Unregisters an event handler that was registered by using <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|<span data-ttu-id="4e3d7-136">移除註冊使用已註冊的事件處理常式<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-136">Unregisters an event handler that was registered by using <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.</span></span>|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|<span data-ttu-id="4e3d7-137">移除註冊使用已註冊的事件處理常式<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-137">Unregisters an event handler that was registered by using <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.</span></span>|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|<span data-ttu-id="4e3d7-138">移除註冊所有已註冊的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-138">Unregisters all registered event handlers.</span></span>|  
  
 <span data-ttu-id="4e3d7-139">如需範例程式碼，請參閱[訂閱使用者介面自動化事件](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)。</span><span class="sxs-lookup"><span data-stu-id="4e3d7-139">For example code, see [Subscribe to UI Automation Events](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3d7-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e3d7-140">See Also</span></span>  
 [<span data-ttu-id="4e3d7-141">訂閱 UI 自動化事件</span><span class="sxs-lookup"><span data-stu-id="4e3d7-141">Subscribe to UI Automation Events</span></span>](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)  
 [<span data-ttu-id="4e3d7-142">UI 自動化事件概觀</span><span class="sxs-lookup"><span data-stu-id="4e3d7-142">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [<span data-ttu-id="4e3d7-143">UI 自動化屬性概觀</span><span class="sxs-lookup"><span data-stu-id="4e3d7-143">UI Automation Properties Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [<span data-ttu-id="4e3d7-144">TrackFocus 範例</span><span class="sxs-lookup"><span data-stu-id="4e3d7-144">TrackFocus Sample</span></span>](http://msdn.microsoft.com/library/4a91c0af-6bb5-4d38-a743-cf136f268fc9)
