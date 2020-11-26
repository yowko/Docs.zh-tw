---
title: 實作 UI 自動化 SelectionItem 控制項模式
description: 請參閱指導方針和慣例，以在消費者介面自動化中執行 SelectionItem 控制項模式。 瞭解 ISelectionItemProvider 介面所需的成員。
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 13bc993f5a18eb6b7dcd96a2a70bc55f5f5cad3e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237452"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a><span data-ttu-id="e7feb-104">實作 UI 自動化 SelectionItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="e7feb-104">Implementing the UI Automation SelectionItem Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="e7feb-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="e7feb-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e7feb-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="e7feb-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e7feb-107">本主題簡介實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e7feb-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="e7feb-108">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="e7feb-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="e7feb-109"><xref:System.Windows.Automation.SelectionItemPattern> 控制項模式用來支援控制項，其支援的控制項作用如同實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>之容器控制項的個別可選取子項目。</span><span class="sxs-lookup"><span data-stu-id="e7feb-109">The <xref:System.Windows.Automation.SelectionItemPattern> control pattern is used to support controls that act as individual, selectable child items of container controls that implement <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="e7feb-110">如需執行 SelectionItem 控制項模式的控制項範例，請參閱 [消費者介面自動化用戶端的控制項模式對應](control-pattern-mapping-for-ui-automation-clients.md)</span><span class="sxs-lookup"><span data-stu-id="e7feb-110">For examples of controls that implement the SelectionItem control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e7feb-111">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="e7feb-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="e7feb-112">實作選取項目控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="e7feb-112">When implementing the Selection Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="e7feb-113">若單一選取控制項有實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>的子控制項，例如 [顯示內容]  對話方塊中的 [螢幕解析度]  滑桿，應實作 <xref:System.Windows.Automation.Provider.ISelectionProvider> ，且其子系應實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> 和 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。</span><span class="sxs-lookup"><span data-stu-id="e7feb-113">Single-selection controls that manage child controls that implement <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, such as the **Screen Resolution** slider in the **Display Properties** dialog box, should implement <xref:System.Windows.Automation.Provider.ISelectionProvider> and their children should implement both <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iselectionitemprovider"></a><span data-ttu-id="e7feb-114">ISelectionItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="e7feb-114">Required Members for ISelectionItemProvider</span></span>  

 <span data-ttu-id="e7feb-115">實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>需要下列屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="e7feb-115">The following properties, methods, and events are required for implementing <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span>  
  
|<span data-ttu-id="e7feb-116">必要成員</span><span class="sxs-lookup"><span data-stu-id="e7feb-116">Required members</span></span>|<span data-ttu-id="e7feb-117">成員類型</span><span class="sxs-lookup"><span data-stu-id="e7feb-117">Member type</span></span>|<span data-ttu-id="e7feb-118">備註</span><span class="sxs-lookup"><span data-stu-id="e7feb-118">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|<span data-ttu-id="e7feb-119">屬性</span><span class="sxs-lookup"><span data-stu-id="e7feb-119">Property</span></span>|<span data-ttu-id="e7feb-120">無</span><span class="sxs-lookup"><span data-stu-id="e7feb-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|<span data-ttu-id="e7feb-121">屬性</span><span class="sxs-lookup"><span data-stu-id="e7feb-121">Property</span></span>|<span data-ttu-id="e7feb-122">無</span><span class="sxs-lookup"><span data-stu-id="e7feb-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|<span data-ttu-id="e7feb-123">方法</span><span class="sxs-lookup"><span data-stu-id="e7feb-123">Method</span></span>|<span data-ttu-id="e7feb-124">無</span><span class="sxs-lookup"><span data-stu-id="e7feb-124">None</span></span>|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|<span data-ttu-id="e7feb-125">事件</span><span class="sxs-lookup"><span data-stu-id="e7feb-125">Event</span></span>|<span data-ttu-id="e7feb-126">當容器中的選項大幅變更，需要傳送比 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> 常數所允許的更多 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> 和 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 事件時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="e7feb-126">Raised when a selection in a container has changed significantly and requires sending more <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> and <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> events than the <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> constant permits.</span></span>|  
  
- <span data-ttu-id="e7feb-127">如果 <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>、 <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>或 <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> 的結果是單一選取的項目，則應引發 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ，否則應視情況傳送 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> 。</span><span class="sxs-lookup"><span data-stu-id="e7feb-127">If the result of a <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, an <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, or a <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> is a single selected item, an <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> should be raised; otherwise send <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> as appropriate.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="e7feb-128">例外狀況</span><span class="sxs-lookup"><span data-stu-id="e7feb-128">Exceptions</span></span>  

 <span data-ttu-id="e7feb-129">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e7feb-129">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="e7feb-130">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="e7feb-130">Exception type</span></span>|<span data-ttu-id="e7feb-131">條件</span><span class="sxs-lookup"><span data-stu-id="e7feb-131">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="e7feb-132">當嘗試下列任一項時：</span><span class="sxs-lookup"><span data-stu-id="e7feb-132">When any of the following are attempted:</span></span><br /><br /> <span data-ttu-id="e7feb-133">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` 。</span><span class="sxs-lookup"><span data-stu-id="e7feb-133">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> is called on a single-selection container where <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` and an element is already selected.</span></span><br /><span data-ttu-id="e7feb-134">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` 。</span><span class="sxs-lookup"><span data-stu-id="e7feb-134">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> is called on a multiple-selection container where <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` and only one element is selected.</span></span><br /><span data-ttu-id="e7feb-135">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` 。</span><span class="sxs-lookup"><span data-stu-id="e7feb-135">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> is called on a single-selection container where <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` and another element is already selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7feb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7feb-136">See also</span></span>

- [<span data-ttu-id="e7feb-137">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="e7feb-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e7feb-138">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="e7feb-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="e7feb-139">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="e7feb-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e7feb-140">實作 UI 自動化 Selection 控制項模式</span><span class="sxs-lookup"><span data-stu-id="e7feb-140">Implementing the UI Automation Selection Control Pattern</span></span>](implementing-the-ui-automation-selection-control-pattern.md)
- [<span data-ttu-id="e7feb-141">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="e7feb-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="e7feb-142">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="e7feb-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- <span data-ttu-id="e7feb-143">[片段提供者範例](/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e7feb-143">[Fragment Provider Sample](/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))</span></span>
