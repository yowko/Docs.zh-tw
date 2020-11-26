---
title: 實作 UI 自動化 Selection 控制項模式
description: 請參閱在消費者介面自動化中執行選取控制項模式的指導方針和慣例。 請參閱 ISelectionProvider 介面所需的成員。
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 7ce6b9765dfd15be320f01151ca0b91393508e55
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237504"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a><span data-ttu-id="8eea9-104">實作 UI 自動化 Selection 控制項模式</span><span class="sxs-lookup"><span data-stu-id="8eea9-104">Implementing the UI Automation Selection Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="8eea9-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="8eea9-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8eea9-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="8eea9-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8eea9-107">本主題將介紹實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8eea9-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>, including information about events and properties.</span></span> <span data-ttu-id="8eea9-108">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="8eea9-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8eea9-109"><xref:System.Windows.Automation.SelectionPattern> 控制項模式是用以支援當作可選取子項目集合的容器使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="8eea9-109">The <xref:System.Windows.Automation.SelectionPattern> control pattern is used to support controls that act as containers for a collection of selectable child items.</span></span> <span data-ttu-id="8eea9-110">這個項目的子系必須實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。</span><span class="sxs-lookup"><span data-stu-id="8eea9-110">The children of this element must implement <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span> <span data-ttu-id="8eea9-111">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="8eea9-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8eea9-112">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="8eea9-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="8eea9-113">實作選取控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="8eea9-113">When implementing the Selection control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8eea9-114">實作 <xref:System.Windows.Automation.Provider.ISelectionProvider> 的控制項允許選取一個或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="8eea9-114">Controls that implement <xref:System.Windows.Automation.Provider.ISelectionProvider> allow either single or multiple child items to be selected.</span></span> <span data-ttu-id="8eea9-115">例如，清單方塊、清單檢視和樹狀檢視都支援多重選取，而下拉式方塊、滑桿和選項按鈕群組則支援單一選取。</span><span class="sxs-lookup"><span data-stu-id="8eea9-115">For example, list box, list view, and tree view support multiple selections whereas combo box, slider, and radio button group support single selection.</span></span>  
  
- <span data-ttu-id="8eea9-116">有最小值、最大值和連續範圍的控制項 (如 [音量]  滑桿控制項)，應實作 <xref:System.Windows.Automation.Provider.IRangeValueProvider> ，而不是實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>。</span><span class="sxs-lookup"><span data-stu-id="8eea9-116">Controls that have a minimum, maximum, and continuous range, such as the **Volume** slider control, should implement <xref:System.Windows.Automation.Provider.IRangeValueProvider> instead of <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span>  
  
- <span data-ttu-id="8eea9-117">單一選取控制項，可管理所執行的子控制項 <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> ，例如 [**顯示內容**] 對話方塊中的 [**螢幕解析度**] 滑杆，或 Microsoft (Word 的 **色彩選擇器** 選取控制項（如下所) 示）， <xref:System.Windows.Automation.Provider.ISelectionProvider> 其子系應執行 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> 和 <xref:System.Windows.Automation.Provider.ISelectionItemProvider> 。</span><span class="sxs-lookup"><span data-stu-id="8eea9-117">Single-selection controls that manage child controls that implement <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, such as the **Screen Resolution** slider in the **Display Properties** dialog box or the **Color Picker** selection control from Microsoft Word (illustrated below), should implement <xref:System.Windows.Automation.Provider.ISelectionProvider>; their children should implement both <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.</span></span>  
  
 <span data-ttu-id="8eea9-118">![已反白顯示黃色的色彩選擇器](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span><span class="sxs-lookup"><span data-stu-id="8eea9-118">![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span></span>  
<span data-ttu-id="8eea9-119">色樣字串對應範例</span><span class="sxs-lookup"><span data-stu-id="8eea9-119">Example of Color Swatch String Mapping</span></span>  
  
- <span data-ttu-id="8eea9-120">功能表不支援 <xref:System.Windows.Automation.SelectionPattern>。</span><span class="sxs-lookup"><span data-stu-id="8eea9-120">Menus do not support <xref:System.Windows.Automation.SelectionPattern>.</span></span> <span data-ttu-id="8eea9-121">如果您使用的功能表項目包括圖形和文字 (例如 Microsoft Outlook 的 [ **View** ] 功能表中的 [**預覽] 窗格** 專案) 而且需要傳達狀態，則應該執行 <xref:System.Windows.Automation.Provider.IToggleProvider> 。</span><span class="sxs-lookup"><span data-stu-id="8eea9-121">If you are working with menu items that include both graphics and text (such as the **Preview Pane** items in the **View** menu in Microsoft Outlook) and need to convey state, you should implement <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
<a name="Required_Members_for_ISelectionProvider"></a>

## <a name="required-members-for-iselectionprovider"></a><span data-ttu-id="8eea9-122">ISelectionProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="8eea9-122">Required Members for ISelectionProvider</span></span>  

 <span data-ttu-id="8eea9-123"><xref:System.Windows.Automation.Provider.ISelectionProvider> 介面需要下列屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="8eea9-123">The following properties, methods, and events are required for the <xref:System.Windows.Automation.Provider.ISelectionProvider> interface.</span></span>  
  
|<span data-ttu-id="8eea9-124">必要成員</span><span class="sxs-lookup"><span data-stu-id="8eea9-124">Required members</span></span>|<span data-ttu-id="8eea9-125">類型</span><span class="sxs-lookup"><span data-stu-id="8eea9-125">Type</span></span>|<span data-ttu-id="8eea9-126">注意</span><span class="sxs-lookup"><span data-stu-id="8eea9-126">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|<span data-ttu-id="8eea9-127">屬性</span><span class="sxs-lookup"><span data-stu-id="8eea9-127">Property</span></span>|<span data-ttu-id="8eea9-128">應支援使用 <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> 和 <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>的屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="8eea9-128">Should support property changed events using <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> and <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|<span data-ttu-id="8eea9-129">屬性</span><span class="sxs-lookup"><span data-stu-id="8eea9-129">Property</span></span>|<span data-ttu-id="8eea9-130">應支援使用 <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> 和 <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>的屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="8eea9-130">Should support property changed events using <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> and <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|<span data-ttu-id="8eea9-131">方法</span><span class="sxs-lookup"><span data-stu-id="8eea9-131">Method</span></span>|<span data-ttu-id="8eea9-132">無</span><span class="sxs-lookup"><span data-stu-id="8eea9-132">None</span></span>|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|<span data-ttu-id="8eea9-133">事件</span><span class="sxs-lookup"><span data-stu-id="8eea9-133">Event</span></span>|<span data-ttu-id="8eea9-134">當容器中的選項大幅變更，需要傳送比 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 常數所允許的更多新增和移除事件時，會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="8eea9-134">Raised when a selection in a container has changed significantly and requires sending more addition and removal events than the <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> constant permits.</span></span>|  
  
 <span data-ttu-id="8eea9-135"><xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> 和 <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> 屬性可以是動態的。</span><span class="sxs-lookup"><span data-stu-id="8eea9-135">The <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> and <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> properties can be dynamic.</span></span> <span data-ttu-id="8eea9-136">例如，控制項的最初狀態可能預設沒有選取任何項目，表示 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8eea9-136">For example, the initial state of a control might not have any items selected by default, indicating that <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> is `false`.</span></span> <span data-ttu-id="8eea9-137">不過，在選取項目之後，控制項就必須至少有一個項目一律保持為選取。</span><span class="sxs-lookup"><span data-stu-id="8eea9-137">However, after an item is selected, the control must always have at least one item selected.</span></span> <span data-ttu-id="8eea9-138">同樣地，在極少數的情況下，控制項可能會允許最初選取多個項目，但之後就只允許單一選取。</span><span class="sxs-lookup"><span data-stu-id="8eea9-138">Similarly, in rare cases, a control might allow multiple items to be selected on initialization, but subsequently allow only single selections to be made.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="8eea9-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8eea9-139">Exceptions</span></span>  

 <span data-ttu-id="8eea9-140">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8eea9-140">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8eea9-141">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="8eea9-141">Exception Type</span></span>|<span data-ttu-id="8eea9-142">條件</span><span class="sxs-lookup"><span data-stu-id="8eea9-142">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<span data-ttu-id="8eea9-143">如果未啟用此控制項。</span><span class="sxs-lookup"><span data-stu-id="8eea9-143">If the control is not enabled.</span></span>|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="8eea9-144">如果隱藏此控制項。</span><span class="sxs-lookup"><span data-stu-id="8eea9-144">If the control is hidden.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8eea9-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eea9-145">See also</span></span>

- [<span data-ttu-id="8eea9-146">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="8eea9-146">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8eea9-147">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="8eea9-147">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8eea9-148">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="8eea9-148">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8eea9-149">實作 UI 自動化 SelectionItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="8eea9-149">Implementing the UI Automation SelectionItem Control Pattern</span></span>](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [<span data-ttu-id="8eea9-150">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="8eea9-150">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="8eea9-151">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="8eea9-151">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
