---
title: 實作 UI 自動化 ExpandCollapse 控制項模式
description: 瞭解 UI 自動化中 ExpandCollapse 控制項模式的執行方針和慣例。 瞭解如何執行 IExpandCollapseProvider。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 525b57816071ba2d879036676201a0506d1a29db
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165855"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a><span data-ttu-id="00684-104">實作 UI 自動化 ExpandCollapse 控制項模式</span><span class="sxs-lookup"><span data-stu-id="00684-104">Implementing the UI Automation ExpandCollapse Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="00684-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="00684-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="00684-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="00684-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="00684-107">本主題簡介實作 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="00684-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="00684-108">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="00684-108">Links to additional references are listed at the end of the overview.</span></span>

<span data-ttu-id="00684-109"><xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式可支援控制項以視覺化方式展開來顯示更多內容和摺疊以隱藏內容。</span><span class="sxs-lookup"><span data-stu-id="00684-109">The <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern is used to support controls that visually expand to display more content and collapse to hide content.</span></span> <span data-ttu-id="00684-110">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="00684-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="00684-111">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="00684-111">Implementation Guidelines and Conventions</span></span>

<span data-ttu-id="00684-112">實作 ExpandCollapse 控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="00684-112">When implementing the ExpandCollapse control pattern, note the following guidelines and conventions:</span></span>

- <span data-ttu-id="00684-113">彙總控制項 - 以提供 UI 展開/摺疊功能的子物件建置 — 必須支援 <xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式，而其子項目並不支援。</span><span class="sxs-lookup"><span data-stu-id="00684-113">Aggregate controls—built with child objects that provide the UI with expand/collapse functionality—must support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern whereas their child elements do not.</span></span> <span data-ttu-id="00684-114">例如，使用清單方塊、按鈕和編輯控制項組合所建置的下拉式方塊控制項，但是它只是必須支援 <xref:System.Windows.Automation.ExpandCollapsePattern>的父下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="00684-114">For example, a combo box control is built with a combination of list box, button, and edit controls, but it is only the parent combo box that must support the <xref:System.Windows.Automation.ExpandCollapsePattern>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="00684-115">例外狀況是功能表控制項，也就是個別 MenuItem 物件的彙總。</span><span class="sxs-lookup"><span data-stu-id="00684-115">An exception is the menu control, which is an aggregate of individual MenuItem objects.</span></span> <span data-ttu-id="00684-116">MenuItem 物件可以支援 <xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式，但是父功能表控制項無法支援。</span><span class="sxs-lookup"><span data-stu-id="00684-116">The MenuItem objects can support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern, but the parent Menu control cannot.</span></span> <span data-ttu-id="00684-117">樹狀結構和樹狀目錄項目控制項適用類似的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00684-117">A similar exception applies to the Tree and Tree Item controls.</span></span>

- <span data-ttu-id="00684-118">當控制項的 <xref:System.Windows.Automation.ExpandCollapseState> 設為 <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>時，控制項的任何 <xref:System.Windows.Automation.ExpandCollapsePattern> 功能目前非使用中，可以使用此控制項模式取得的唯一資訊是 <xref:System.Windows.Automation.ExpandCollapseState>。</span><span class="sxs-lookup"><span data-stu-id="00684-118">When the <xref:System.Windows.Automation.ExpandCollapseState> of a control is set to <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, any <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is currently inactive for the control and the only information that can be obtained using this control pattern is the <xref:System.Windows.Automation.ExpandCollapseState>.</span></span> <span data-ttu-id="00684-119">如果後續新增任何子物件， <xref:System.Windows.Automation.ExpandCollapseState> 會變更且 <xref:System.Windows.Automation.ExpandCollapsePattern> 功能會啟動。</span><span class="sxs-lookup"><span data-stu-id="00684-119">If any child objects are subsequently added, the <xref:System.Windows.Automation.ExpandCollapseState> changes and <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is activated.</span></span>

- <span data-ttu-id="00684-120"><xref:System.Windows.Automation.ExpandCollapseState> 是指僅限直屬子物件的可見度，而非所有子系物件的可見度。</span><span class="sxs-lookup"><span data-stu-id="00684-120"><xref:System.Windows.Automation.ExpandCollapseState> refers to the visibility of immediate child objects only; it does not refer to the visibility of all descendant objects.</span></span>

- <span data-ttu-id="00684-121">展開和摺疊功能是控制項專屬功能。</span><span class="sxs-lookup"><span data-stu-id="00684-121">Expand and Collapse functionality is control-specific.</span></span> <span data-ttu-id="00684-122">以下是此行為的範例：</span><span class="sxs-lookup"><span data-stu-id="00684-122">The following are examples of this behavior.</span></span>

  - <span data-ttu-id="00684-123">Office 個人功能表可以是三種狀態 MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>、 <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> 和 <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>)，其中控制項會指定當呼叫 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 時要採用的狀態。</span><span class="sxs-lookup"><span data-stu-id="00684-123">The Office Personal Menu can be a tri-state MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> and <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) where the control specifies the state to adopt when an <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called.</span></span>

  - <span data-ttu-id="00684-124">在 TreeItem 上呼叫 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 可能會顯示所有子代或只顯示直屬子系。</span><span class="sxs-lookup"><span data-stu-id="00684-124">Calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> on a TreeItem may display all descendants or only immediate children.</span></span>

  - <span data-ttu-id="00684-125">如果在控制項上呼叫 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 會維護其子代的狀態，應該會傳送可見度變更事件，如果父控制項在摺疊時不會維護其子代的狀態，則不是狀態變更事件，控制項可能會終結所有不再顯示的子代，並引發已終結事件，或者它可能會針對每個子代變更 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> 並且引發可見度變更事件。</span><span class="sxs-lookup"><span data-stu-id="00684-125">If calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> on a control maintains the state of its descendants, a visibility change event should be sent, not a state change event If the parent control does not maintain the state of its descendants when collapsed, the control may destroy all the descendants that are no longer visible and raise a destroyed event; or it may change the <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> for each descendant and raise a visibility change event.</span></span>

- <span data-ttu-id="00684-126">若要保證導覽功能，物件最好是位於 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中 (具有適當的可見度狀態)，不論其父系 <xref:System.Windows.Automation.ExpandCollapseState>為何。</span><span class="sxs-lookup"><span data-stu-id="00684-126">To guarantee navigation, it is desirable for an object to be in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree (with appropriate visibility state) regardless of its parents <xref:System.Windows.Automation.ExpandCollapseState>.</span></span> <span data-ttu-id="00684-127">如果子代是隨選產生，則它們只有在第一次顯示或可見時，才會出現在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="00684-127">If descendants are generated on demand, they may only appear in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree after being displayed for the first time or only while they are visible.</span></span>

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a><span data-ttu-id="00684-128">IExpandCollapseProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="00684-128">Required Members for IExpandCollapseProvider</span></span>

<span data-ttu-id="00684-129">以下是實作 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="00684-129">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.</span></span>

|<span data-ttu-id="00684-130">必要成員</span><span class="sxs-lookup"><span data-stu-id="00684-130">Required members</span></span>|<span data-ttu-id="00684-131">成員類型</span><span class="sxs-lookup"><span data-stu-id="00684-131">Member type</span></span>|<span data-ttu-id="00684-132">注意</span><span class="sxs-lookup"><span data-stu-id="00684-132">Notes</span></span>|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|<span data-ttu-id="00684-133">屬性</span><span class="sxs-lookup"><span data-stu-id="00684-133">Property</span></span>|<span data-ttu-id="00684-134">None</span><span class="sxs-lookup"><span data-stu-id="00684-134">None</span></span>|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|<span data-ttu-id="00684-135">方法</span><span class="sxs-lookup"><span data-stu-id="00684-135">Method</span></span>|<span data-ttu-id="00684-136">None</span><span class="sxs-lookup"><span data-stu-id="00684-136">None</span></span>|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|<span data-ttu-id="00684-137">方法</span><span class="sxs-lookup"><span data-stu-id="00684-137">Method</span></span>|<span data-ttu-id="00684-138">None</span><span class="sxs-lookup"><span data-stu-id="00684-138">None</span></span>|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|<span data-ttu-id="00684-139">事件</span><span class="sxs-lookup"><span data-stu-id="00684-139">Event</span></span>|<span data-ttu-id="00684-140">此控制項沒有相關聯的事件；使用這個泛型委派。</span><span class="sxs-lookup"><span data-stu-id="00684-140">This control has no associated events; use this generic delegate.</span></span>|

<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="00684-141">例外狀況</span><span class="sxs-lookup"><span data-stu-id="00684-141">Exceptions</span></span>

<span data-ttu-id="00684-142">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00684-142">Providers must throw the following exceptions.</span></span>

|<span data-ttu-id="00684-143">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="00684-143">Exception type</span></span>|<span data-ttu-id="00684-144">條件</span><span class="sxs-lookup"><span data-stu-id="00684-144">Condition</span></span>|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<span data-ttu-id="00684-145">當 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 時會呼叫 <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>。</span><span class="sxs-lookup"><span data-stu-id="00684-145">Either <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called when the <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.</span></span>|

## <a name="see-also"></a><span data-ttu-id="00684-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00684-146">See also</span></span>

- [<span data-ttu-id="00684-147">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="00684-147">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="00684-148">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="00684-148">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="00684-149">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="00684-149">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="00684-150">使用 TreeWalker 巡覽 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="00684-150">Navigate Among UI Automation Elements with TreeWalker</span></span>](navigate-among-ui-automation-elements-with-treewalker.md)
- [<span data-ttu-id="00684-151">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="00684-151">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="00684-152">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="00684-152">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
