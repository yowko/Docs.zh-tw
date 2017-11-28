---
title: "實作 UI 自動化 Dock 控制項模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 68c3dcdb1d8f15f312dea40ae59a3b1a4736c484
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="8846f-102">實作 UI 自動化 Dock 控制項模式</span><span class="sxs-lookup"><span data-stu-id="8846f-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="8846f-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="8846f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8846f-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="8846f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8846f-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IDockProvider>的方針和慣例，包括屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8846f-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="8846f-106">其他參考的連結列於此主題的結尾部分。</span><span class="sxs-lookup"><span data-stu-id="8846f-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8846f-107"><xref:System.Windows.Automation.DockPattern> 控制項模式是用來公開停駐容器內控制項的停駐屬性。</span><span class="sxs-lookup"><span data-stu-id="8846f-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="8846f-108">停駐容器是一種控制項，可讓您依垂直和水平的相對位置排列子項目。</span><span class="sxs-lookup"><span data-stu-id="8846f-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="8846f-109">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="8846f-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="8846f-110">![具有兩個停駐的子系的停駐容器。] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="8846f-110">![Docking container with two docked children.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="8846f-111">Visual Studio 的停駐範例，其中「類別檢視」視窗是 DockPosition.Right，「錯誤清單」視窗是 DockPosition.Bottom</span><span class="sxs-lookup"><span data-stu-id="8846f-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8846f-112">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="8846f-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8846f-113">實作停駐控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="8846f-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="8846f-114"><xref:System.Windows.Automation.Provider.IDockProvider> 不會公開停駐容器的任何屬性，而對於停駐容器內與目前控制項相鄰的停駐控制項，也不會公開其任何屬性。</span><span class="sxs-lookup"><span data-stu-id="8846f-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
-   <span data-ttu-id="8846f-115">控制項會根據其目前的疊置順序，在彼此相對的位置停駐；疊置順序的位置愈高，控制項離停駐容器的指定邊緣就愈遠。</span><span class="sxs-lookup"><span data-stu-id="8846f-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
-   <span data-ttu-id="8846f-116">如果停駐容器可以調整大小，容器內的任何停駐控制項會再次對齊到原始停駐的相同邊緣。</span><span class="sxs-lookup"><span data-stu-id="8846f-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="8846f-117">停駐的控制項也會根據其 <xref:System.Windows.Automation.DockPosition>的停駐行為，調整大小來填滿容器內的任何空間。</span><span class="sxs-lookup"><span data-stu-id="8846f-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="8846f-118">例如，如果指定 <xref:System.Windows.Automation.DockPosition.Top> ，控制項的左右兩邊就會擴展來填滿任何可用的空間。</span><span class="sxs-lookup"><span data-stu-id="8846f-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="8846f-119">如果指定 <xref:System.Windows.Automation.DockPosition.Fill> ，則控制項的四個邊將會擴展來填滿任何可用的空間。</span><span class="sxs-lookup"><span data-stu-id="8846f-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
-   <span data-ttu-id="8846f-120">在多監視器系統上，控制項應停駐到目前監視器的左或右邊。</span><span class="sxs-lookup"><span data-stu-id="8846f-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="8846f-121">若不可行，則應停駐到最左邊監視器的左邊，或最右邊監視器的右邊。</span><span class="sxs-lookup"><span data-stu-id="8846f-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="8846f-122">IDockProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="8846f-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="8846f-123">以下是實作 IDockProvider 介面的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="8846f-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="8846f-124">必要成員</span><span class="sxs-lookup"><span data-stu-id="8846f-124">Required members</span></span>|<span data-ttu-id="8846f-125">成員類型</span><span class="sxs-lookup"><span data-stu-id="8846f-125">Member type</span></span>|<span data-ttu-id="8846f-126">備註</span><span class="sxs-lookup"><span data-stu-id="8846f-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="8846f-127">屬性</span><span class="sxs-lookup"><span data-stu-id="8846f-127">Property</span></span>|<span data-ttu-id="8846f-128">無</span><span class="sxs-lookup"><span data-stu-id="8846f-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="8846f-129">方法</span><span class="sxs-lookup"><span data-stu-id="8846f-129">Method</span></span>|<span data-ttu-id="8846f-130">無</span><span class="sxs-lookup"><span data-stu-id="8846f-130">None</span></span>|  
  
 <span data-ttu-id="8846f-131">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="8846f-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8846f-132">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8846f-132">Exceptions</span></span>  
 <span data-ttu-id="8846f-133">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8846f-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8846f-134">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="8846f-134">Exception type</span></span>|<span data-ttu-id="8846f-135">條件</span><span class="sxs-lookup"><span data-stu-id="8846f-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="8846f-136">-當控制項不是無法執行要求的停駐樣式。</span><span class="sxs-lookup"><span data-stu-id="8846f-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8846f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8846f-137">See Also</span></span>  
 [<span data-ttu-id="8846f-138">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="8846f-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="8846f-139">UI 自動化提供者不支援控制項模式</span><span class="sxs-lookup"><span data-stu-id="8846f-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="8846f-140">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="8846f-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="8846f-141">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="8846f-141">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="8846f-142">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="8846f-142">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
