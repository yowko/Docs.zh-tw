---
title: 實作 UI 自動化 Scroll 控制項模式
description: 請參閱在消費者介面自動化中執行捲軸控制項模式的指導方針和慣例。 請參閱 IScrollProvider 介面所需的成員。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 4069772530d8b4db817aa1b7a9be86a3ee83881e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239259"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a><span data-ttu-id="04fc0-104">實作 UI 自動化 Scroll 控制項模式</span><span class="sxs-lookup"><span data-stu-id="04fc0-104">Implementing the UI Automation Scroll Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="04fc0-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="04fc0-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="04fc0-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="04fc0-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="04fc0-107">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IScrollProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="04fc0-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IScrollProvider>, including information about events and properties.</span></span> <span data-ttu-id="04fc0-108">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="04fc0-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="04fc0-109"><xref:System.Windows.Automation.ScrollPattern> 控制項模式是用來支援放有一組子項目的捲動式容器控制項。</span><span class="sxs-lookup"><span data-stu-id="04fc0-109">The <xref:System.Windows.Automation.ScrollPattern> control pattern is used to support a control that acts as a scrollable container for a collection of child objects.</span></span> <span data-ttu-id="04fc0-110">控制項不一定要使用捲軸才能支援捲動功能，不過它通常會這麼做。</span><span class="sxs-lookup"><span data-stu-id="04fc0-110">The control is not required to use scrollbars to support the scrolling functionality, although it commonly does.</span></span>  
  
 <span data-ttu-id="04fc0-111">![不含捲軸的 Scroll 控制項。](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")</span><span class="sxs-lookup"><span data-stu-id="04fc0-111">![Scroll control without scrollbars.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")</span></span>  
<span data-ttu-id="04fc0-112">不使用捲軸的捲動控制項範例</span><span class="sxs-lookup"><span data-stu-id="04fc0-112">Example of a Scrolling Control that Does Not Use Scrollbars</span></span>  
  
 <span data-ttu-id="04fc0-113">如需實作此控制項的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="04fc0-113">For examples of controls that implement this control, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="04fc0-114">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="04fc0-114">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="04fc0-115">實作捲軸控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="04fc0-115">When implementing the Scroll control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="04fc0-116">這個控制項的子系必須實作 <xref:System.Windows.Automation.Provider.IScrollItemProvider>。</span><span class="sxs-lookup"><span data-stu-id="04fc0-116">The children of this control must implement <xref:System.Windows.Automation.Provider.IScrollItemProvider>.</span></span>  
  
- <span data-ttu-id="04fc0-117">容器控制項的捲軸不支援 <xref:System.Windows.Automation.ScrollPattern> 控制項模式。</span><span class="sxs-lookup"><span data-stu-id="04fc0-117">The scrollbars of a container control do not support the <xref:System.Windows.Automation.ScrollPattern> control pattern.</span></span> <span data-ttu-id="04fc0-118">捲軸必須改成支援 <xref:System.Windows.Automation.RangeValuePattern> 控制項模式。</span><span class="sxs-lookup"><span data-stu-id="04fc0-118">They must support the <xref:System.Windows.Automation.RangeValuePattern> control pattern instead.</span></span>  
  
- <span data-ttu-id="04fc0-119">若捲動是以百分比為單位，則與捲動刻度相關的所有值或數量必須標準化為 0 到 100 之間的範圍。</span><span class="sxs-lookup"><span data-stu-id="04fc0-119">When scrolling is measured in percentages, all values or amounts related to scroll graduation must be normalized to a range of 0 to 100.</span></span>  
  
- <span data-ttu-id="04fc0-120"><xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> 和 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> 與 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>無關。</span><span class="sxs-lookup"><span data-stu-id="04fc0-120"><xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> and <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> are independent of the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.</span></span>  
  
- <span data-ttu-id="04fc0-121">如果 <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> = `false` ，則 <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> 應設為 100%，而且 <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> 應設為 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>。</span><span class="sxs-lookup"><span data-stu-id="04fc0-121">If <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> = `false` then <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> should be set to 100% and <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> should be set to <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>.</span></span> <span data-ttu-id="04fc0-122">同樣地，如果 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> = `false` ，則 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> 應設為 100%，而且 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> 應設為 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>。</span><span class="sxs-lookup"><span data-stu-id="04fc0-122">Likewise, if <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> = `false` then <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> should be set to 100 percent and <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> should be set to <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>.</span></span> <span data-ttu-id="04fc0-123">若用戶端不想捲動的方向啟動時，這可讓使用者介面自動化用戶端在 <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> 方法中使用這些屬性值，以免發生 [競爭情形](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) 。</span><span class="sxs-lookup"><span data-stu-id="04fc0-123">This allows a UI Automation client to use these property values within the <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> method while avoiding a [race condition](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) if a direction the client is not interested in scrolling becomes activated.</span></span>  
  
- <span data-ttu-id="04fc0-124"><xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> 是地區設定特性。</span><span class="sxs-lookup"><span data-stu-id="04fc0-124"><xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> is locale-specific.</span></span> <span data-ttu-id="04fc0-125">設定 HorizontalScrollPercent = 100.0 時，必須將控制項的捲動位置設為由左至右語言 (如英文) 的最右側位置。</span><span class="sxs-lookup"><span data-stu-id="04fc0-125">Setting HorizontalScrollPercent = 100.0 must set the scrolling location of the control to the equivalent of its rightmost position for languages such as English that read left to right.</span></span> <span data-ttu-id="04fc0-126">相反地，若為由右至左語言 (如阿拉伯文)，設定 HorizontalScrollPercent = 100.0 時，必須將捲動位置設為最左側位置。</span><span class="sxs-lookup"><span data-stu-id="04fc0-126">Alternately, for languages such as Arabic that read right to left, setting HorizontalScrollPercent = 100.0 must set the scroll location to the leftmost position.</span></span>  
  
<a name="Required_Members_for_IScrollProvider"></a>

## <a name="required-members-for-iscrollprovider"></a><span data-ttu-id="04fc0-127">IScrollProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="04fc0-127">Required Members for IScrollProvider</span></span>  

 <span data-ttu-id="04fc0-128">以下是實作 <xref:System.Windows.Automation.Provider.IScrollProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="04fc0-128">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span>  
  
|<span data-ttu-id="04fc0-129">必要成員</span><span class="sxs-lookup"><span data-stu-id="04fc0-129">Required member</span></span>|<span data-ttu-id="04fc0-130">成員類型</span><span class="sxs-lookup"><span data-stu-id="04fc0-130">Member type</span></span>|<span data-ttu-id="04fc0-131">備註</span><span class="sxs-lookup"><span data-stu-id="04fc0-131">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|<span data-ttu-id="04fc0-132">屬性</span><span class="sxs-lookup"><span data-stu-id="04fc0-132">Property</span></span>|<span data-ttu-id="04fc0-133">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|<span data-ttu-id="04fc0-134">屬性</span><span class="sxs-lookup"><span data-stu-id="04fc0-134">Property</span></span>|<span data-ttu-id="04fc0-135">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-135">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|<span data-ttu-id="04fc0-136">屬性</span><span class="sxs-lookup"><span data-stu-id="04fc0-136">Property</span></span>|<span data-ttu-id="04fc0-137">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-137">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|<span data-ttu-id="04fc0-138">屬性</span><span class="sxs-lookup"><span data-stu-id="04fc0-138">Property</span></span>|<span data-ttu-id="04fc0-139">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-139">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|<span data-ttu-id="04fc0-140">屬性</span><span class="sxs-lookup"><span data-stu-id="04fc0-140">Property</span></span>|<span data-ttu-id="04fc0-141">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-141">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|<span data-ttu-id="04fc0-142">屬性</span><span class="sxs-lookup"><span data-stu-id="04fc0-142">Property</span></span>|<span data-ttu-id="04fc0-143">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-143">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|<span data-ttu-id="04fc0-144">方法</span><span class="sxs-lookup"><span data-stu-id="04fc0-144">Method</span></span>|<span data-ttu-id="04fc0-145">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-145">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|<span data-ttu-id="04fc0-146">方法</span><span class="sxs-lookup"><span data-stu-id="04fc0-146">Method</span></span>|<span data-ttu-id="04fc0-147">無</span><span class="sxs-lookup"><span data-stu-id="04fc0-147">None</span></span>|  
  
 <span data-ttu-id="04fc0-148">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="04fc0-148">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="04fc0-149">例外狀況</span><span class="sxs-lookup"><span data-stu-id="04fc0-149">Exceptions</span></span>  

 <span data-ttu-id="04fc0-150">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="04fc0-150">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="04fc0-151">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="04fc0-151">Exception Type</span></span>|<span data-ttu-id="04fc0-152">條件</span><span class="sxs-lookup"><span data-stu-id="04fc0-152">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="04fc0-153">如果控制項僅支援垂直或水平捲動的<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> 值，但傳入了 <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> 值， <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> 就會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="04fc0-153"><xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> throws this exception if a control supports <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> values exclusively for horizontal or vertical scrolling, but a <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> value is passed in.</span></span>|  
|<xref:System.ArgumentException>|<span data-ttu-id="04fc0-154">當傳入無法轉換成雙精度浮點數的值時，<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> 便會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="04fc0-154"><xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> throws this exception when a value that cannot be converted to a double is passed in.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="04fc0-155">當傳入大於 100 或小於 0 的值 (-1 例外，因為它相當於<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> ) 時， <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>就會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="04fc0-155"><xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> throws this exception when a value greater than 100 or less than 0 is passed in (except -1 which is equivalent to <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).</span></span>|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="04fc0-156">嘗試在不支援的方向捲動時， <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> 和 <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> 都會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="04fc0-156">Both <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> and <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> throw this exception when an attempt is made to scroll in an unsupported direction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04fc0-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04fc0-157">See also</span></span>

- [<span data-ttu-id="04fc0-158">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="04fc0-158">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="04fc0-159">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="04fc0-159">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="04fc0-160">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="04fc0-160">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="04fc0-161">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="04fc0-161">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="04fc0-162">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="04fc0-162">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
