---
title: "實作 UI 自動化 SelectionItem 控制項模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5722896b1f1b8b639152179194668105d8fafdf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a><span data-ttu-id="b4bce-102">實作 UI 自動化 SelectionItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="b4bce-102">Implementing the UI Automation SelectionItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="b4bce-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="b4bce-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b4bce-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="b4bce-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b4bce-105">本主題簡介實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b4bce-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="b4bce-106">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="b4bce-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="b4bce-107"><xref:System.Windows.Automation.SelectionItemPattern> 控制項模式用來支援控制項，其支援的控制項作用如同實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>之容器控制項的個別可選取子項目。</span><span class="sxs-lookup"><span data-stu-id="b4bce-107">The <xref:System.Windows.Automation.SelectionItemPattern> control pattern is used to support controls that act as individual, selectable child items of container controls that implement <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="b4bce-108">如需實作選取項目控制項模式的控制項範例，請參閱[UI 自動化用戶端的控制項模式對應](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)</span><span class="sxs-lookup"><span data-stu-id="b4bce-108">For examples of controls that implement the SelectionItem control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b4bce-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="b4bce-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b4bce-110">實作選取項目控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="b4bce-110">When implementing the Selection Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="b4bce-111">若單一選取控制項有實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>的子控制項，例如 [顯示內容]  對話方塊中的 [螢幕解析度]  滑桿，應實作 <xref:System.Windows.Automation.Provider.ISelectionProvider> ，且其子系應實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> 和 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。</span><span class="sxs-lookup"><span data-stu-id="b4bce-111">Single-selection controls that manage child controls that implement <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, such as the **Screen Resolution** slider in the **Display Properties** dialog box, should implement <xref:System.Windows.Automation.Provider.ISelectionProvider> and their children should implement both <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a><span data-ttu-id="b4bce-112">ISelectionItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="b4bce-112">Required Members for ISelectionItemProvider</span></span>  
 <span data-ttu-id="b4bce-113">實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>需要下列屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="b4bce-113">The following properties, methods, and events are required for implementing <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span>  
  
|<span data-ttu-id="b4bce-114">必要成員</span><span class="sxs-lookup"><span data-stu-id="b4bce-114">Required members</span></span>|<span data-ttu-id="b4bce-115">成員類型</span><span class="sxs-lookup"><span data-stu-id="b4bce-115">Member type</span></span>|<span data-ttu-id="b4bce-116">備註</span><span class="sxs-lookup"><span data-stu-id="b4bce-116">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|<span data-ttu-id="b4bce-117">屬性</span><span class="sxs-lookup"><span data-stu-id="b4bce-117">Property</span></span>|<span data-ttu-id="b4bce-118">無</span><span class="sxs-lookup"><span data-stu-id="b4bce-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|<span data-ttu-id="b4bce-119">屬性</span><span class="sxs-lookup"><span data-stu-id="b4bce-119">Property</span></span>|<span data-ttu-id="b4bce-120">無</span><span class="sxs-lookup"><span data-stu-id="b4bce-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|<span data-ttu-id="b4bce-121">方法</span><span class="sxs-lookup"><span data-stu-id="b4bce-121">Method</span></span>|<span data-ttu-id="b4bce-122">無</span><span class="sxs-lookup"><span data-stu-id="b4bce-122">None</span></span>|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|<span data-ttu-id="b4bce-123">事件</span><span class="sxs-lookup"><span data-stu-id="b4bce-123">Event</span></span>|<span data-ttu-id="b4bce-124">當容器中的選項大幅變更，需要傳送比 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> 常數所允許的更多 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> 和 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 事件時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="b4bce-124">Raised when a selection in a container has changed significantly and requires sending more <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> and <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> events than the <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> constant permits.</span></span>|  
  
-   <span data-ttu-id="b4bce-125">如果 <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>、 <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>或 <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> 的結果是單一選取的項目，則應引發 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ，否則應視情況傳送 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> 。</span><span class="sxs-lookup"><span data-stu-id="b4bce-125">If the result of a <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, an <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, or a <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> is a single selected item, an <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> should be raised; otherwise send <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> as appropriate.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b4bce-126">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b4bce-126">Exceptions</span></span>  
 <span data-ttu-id="b4bce-127">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b4bce-127">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b4bce-128">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="b4bce-128">Exception type</span></span>|<span data-ttu-id="b4bce-129">條件</span><span class="sxs-lookup"><span data-stu-id="b4bce-129">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="b4bce-130">當嘗試下列任一項時：</span><span class="sxs-lookup"><span data-stu-id="b4bce-130">When any of the following are attempted:</span></span><br /><br /> <span data-ttu-id="b4bce-131">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>單一選取容器上呼叫其中<xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true`且已選取項目。</span><span class="sxs-lookup"><span data-stu-id="b4bce-131">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> is called on a single-selection container where <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` and an element is already selected.</span></span><br /><span data-ttu-id="b4bce-132">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` 。</span><span class="sxs-lookup"><span data-stu-id="b4bce-132">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> is called on a multiple-selection container where <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` and only one element is selected.</span></span><br /><span data-ttu-id="b4bce-133">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` 。</span><span class="sxs-lookup"><span data-stu-id="b4bce-133">-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> is called on a single-selection container where <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` and another element is already selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4bce-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4bce-134">See Also</span></span>  
 [<span data-ttu-id="b4bce-135">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="b4bce-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="b4bce-136">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="b4bce-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="b4bce-137">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="b4bce-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="b4bce-138">實作 UI 自動化 Selection 控制項模式</span><span class="sxs-lookup"><span data-stu-id="b4bce-138">Implementing the UI Automation Selection Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)  
 [<span data-ttu-id="b4bce-139">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="b4bce-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="b4bce-140">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="b4bce-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [<span data-ttu-id="b4bce-141">片段提供者範例</span><span class="sxs-lookup"><span data-stu-id="b4bce-141">Fragment Provider Sample</span></span>](http://msdn.microsoft.com/en-us/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
