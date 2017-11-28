---
title: "實作 UI 自動化 Window 控制項模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9e8d83c3ef40ccc6e97ba3128cab5d88a5af5305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="7c521-102">實作 UI 自動化 Window 控制項模式</span><span class="sxs-lookup"><span data-stu-id="7c521-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="7c521-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="7c521-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7c521-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="7c521-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7c521-105">本主題簡介實作 <xref:System.Windows.Automation.Provider.IWindowProvider>的方針和慣例，包括 <xref:System.Windows.Automation.WindowPattern> 屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7c521-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="7c521-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="7c521-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="7c521-107"><xref:System.Windows.Automation.WindowPattern> 控制項模式是用來支援在傳統 [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]內提供基本視窗功能的控制項。</span><span class="sxs-lookup"><span data-stu-id="7c521-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span></span> <span data-ttu-id="7c521-108">必須實作此控制項模式的控制項範例包括最上層應用程式視窗、 [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] 子視窗、可調整大小的分割窗格控制項、強制回應對話方塊和氣球說明視窗。</span><span class="sxs-lookup"><span data-stu-id="7c521-108">Examples of controls that must implement this control pattern include top-level application windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7c521-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="7c521-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="7c521-110">實作視窗控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="7c521-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="7c521-111">為能夠使用使用者介面自動化修改視窗大小和螢幕位置，控制項除了必須實作 <xref:System.Windows.Automation.Provider.ITransformProvider> 之外，還必須實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="7c521-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="7c521-112">若控制項包含可讓它移動、調整大小、最大化、最小化或關閉的標題列和標題列項目，通常必須實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="7c521-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="7c521-113">工具提示快顯視窗和下拉式方塊或下拉式功能表等控制項通常不會實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="7c521-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="7c521-114">氣球說明視窗與基本工具提示快顯視窗的不同之處，在於前者提供了類似視窗的 [關閉] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7c521-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
-   <span data-ttu-id="7c521-115">IWindowProvider 不支援全螢幕模式，因為它對應用程式是功能特定的，而不是典型的視窗行為。</span><span class="sxs-lookup"><span data-stu-id="7c521-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="7c521-116">IWindowProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="7c521-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="7c521-117">IWindowProvider 介面需要下列屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="7c521-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="7c521-118">必要成員</span><span class="sxs-lookup"><span data-stu-id="7c521-118">Required member</span></span>|<span data-ttu-id="7c521-119">成員類型</span><span class="sxs-lookup"><span data-stu-id="7c521-119">Member type</span></span>|<span data-ttu-id="7c521-120">備註</span><span class="sxs-lookup"><span data-stu-id="7c521-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="7c521-121">屬性</span><span class="sxs-lookup"><span data-stu-id="7c521-121">Property</span></span>|<span data-ttu-id="7c521-122">無</span><span class="sxs-lookup"><span data-stu-id="7c521-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="7c521-123">屬性</span><span class="sxs-lookup"><span data-stu-id="7c521-123">Property</span></span>|<span data-ttu-id="7c521-124">無</span><span class="sxs-lookup"><span data-stu-id="7c521-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="7c521-125">屬性</span><span class="sxs-lookup"><span data-stu-id="7c521-125">Property</span></span>|<span data-ttu-id="7c521-126">無</span><span class="sxs-lookup"><span data-stu-id="7c521-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="7c521-127">屬性</span><span class="sxs-lookup"><span data-stu-id="7c521-127">Property</span></span>|<span data-ttu-id="7c521-128">無</span><span class="sxs-lookup"><span data-stu-id="7c521-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="7c521-129">屬性</span><span class="sxs-lookup"><span data-stu-id="7c521-129">Property</span></span>|<span data-ttu-id="7c521-130">無</span><span class="sxs-lookup"><span data-stu-id="7c521-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="7c521-131">屬性</span><span class="sxs-lookup"><span data-stu-id="7c521-131">Property</span></span>|<span data-ttu-id="7c521-132">無</span><span class="sxs-lookup"><span data-stu-id="7c521-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="7c521-133">方法</span><span class="sxs-lookup"><span data-stu-id="7c521-133">Method</span></span>|<span data-ttu-id="7c521-134">無</span><span class="sxs-lookup"><span data-stu-id="7c521-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="7c521-135">方法</span><span class="sxs-lookup"><span data-stu-id="7c521-135">Method</span></span>|<span data-ttu-id="7c521-136">無</span><span class="sxs-lookup"><span data-stu-id="7c521-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="7c521-137">方法</span><span class="sxs-lookup"><span data-stu-id="7c521-137">Method</span></span>|<span data-ttu-id="7c521-138">無</span><span class="sxs-lookup"><span data-stu-id="7c521-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="7c521-139">事件</span><span class="sxs-lookup"><span data-stu-id="7c521-139">Event</span></span>|<span data-ttu-id="7c521-140">無</span><span class="sxs-lookup"><span data-stu-id="7c521-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="7c521-141">事件</span><span class="sxs-lookup"><span data-stu-id="7c521-141">Event</span></span>|<span data-ttu-id="7c521-142">無</span><span class="sxs-lookup"><span data-stu-id="7c521-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="7c521-143">事件</span><span class="sxs-lookup"><span data-stu-id="7c521-143">Event</span></span>|<span data-ttu-id="7c521-144">不保證是 <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="7c521-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="7c521-145">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7c521-145">Exceptions</span></span>  
 <span data-ttu-id="7c521-146">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7c521-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="7c521-147">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="7c521-147">Exception type</span></span>|<span data-ttu-id="7c521-148">條件</span><span class="sxs-lookup"><span data-stu-id="7c521-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="7c521-149">-當控制項不支援要求的行為。</span><span class="sxs-lookup"><span data-stu-id="7c521-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="7c521-150">-當參數不是有效的數字。</span><span class="sxs-lookup"><span data-stu-id="7c521-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c521-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c521-151">See Also</span></span>  
 [<span data-ttu-id="7c521-152">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="7c521-152">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="7c521-153">UI 自動化提供者不支援控制項模式</span><span class="sxs-lookup"><span data-stu-id="7c521-153">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="7c521-154">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="7c521-154">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="7c521-155">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="7c521-155">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="7c521-156">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="7c521-156">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
