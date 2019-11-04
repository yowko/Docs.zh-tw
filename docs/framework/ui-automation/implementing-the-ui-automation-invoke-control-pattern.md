---
title: 實作 UI 自動化 Invoke 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: 616bbab4d659cf00b1f730492e73ad6b847e3926
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458010"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a><span data-ttu-id="81b54-102">實作 UI 自動化 Invoke 控制項模式</span><span class="sxs-lookup"><span data-stu-id="81b54-102">Implementing the UI Automation Invoke Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="81b54-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="81b54-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="81b54-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="81b54-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>

<span data-ttu-id="81b54-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IInvokeProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="81b54-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IInvokeProvider>, including information about events and properties.</span></span> <span data-ttu-id="81b54-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="81b54-106">Links to additional references are listed at the end of the topic.</span></span>

<span data-ttu-id="81b54-107"><xref:System.Windows.Automation.InvokePattern> 控制項模式用來支援控制項，且這些控制項在啟動時並不會維護狀態，而是會啟始或執行明確的單一動作。</span><span class="sxs-lookup"><span data-stu-id="81b54-107">The <xref:System.Windows.Automation.InvokePattern> control pattern is used to support controls that do not maintain state when activated but rather initiate or perform a single, unambiguous action.</span></span> <span data-ttu-id="81b54-108">維護狀態的控制項，例如核取方塊和選項按鈕，必須分別實作 <xref:System.Windows.Automation.Provider.IToggleProvider> 及 <xref:System.Windows.Automation.Provider.ISelectionItemProvider> 。</span><span class="sxs-lookup"><span data-stu-id="81b54-108">Controls that do maintain state, such as check boxes and radio buttons, must instead implement <xref:System.Windows.Automation.Provider.IToggleProvider> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider> respectively.</span></span> <span data-ttu-id="81b54-109">如需實作叫用控制項模式的控制項，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="81b54-109">For examples of controls that implement the Invoke control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="81b54-110">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="81b54-110">Implementation Guidelines and Conventions</span></span>

<span data-ttu-id="81b54-111">實作叫用控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="81b54-111">When implementing the Invoke control pattern, note the following guidelines and conventions:</span></span>

- <span data-ttu-id="81b54-112">如果未透過另一個控制項模式提供者來公開相同的行為，則控制項會實作 <xref:System.Windows.Automation.Provider.IInvokeProvider> 。</span><span class="sxs-lookup"><span data-stu-id="81b54-112">Controls implement <xref:System.Windows.Automation.Provider.IInvokeProvider> if the same behavior is not exposed through another control pattern provider.</span></span> <span data-ttu-id="81b54-113">例如，如果控制項的 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 方法所執行的動作與 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 方法相同，該控制項就不應實作 <xref:System.Windows.Automation.Provider.IInvokeProvider>。</span><span class="sxs-lookup"><span data-stu-id="81b54-113">For example, if the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method on a control performs the same action as the <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> method, the control should not implement <xref:System.Windows.Automation.Provider.IInvokeProvider>.</span></span>

- <span data-ttu-id="81b54-114">通常按一下、按兩下或按 ENTER、使用預先定義的鍵盤快速鍵，或其他按鈕組合，就可以叫用控制項。</span><span class="sxs-lookup"><span data-stu-id="81b54-114">Invoking a control is generally performed by clicking or double-clicking or pressing ENTER, a predefined keyboard shortcut, or some alternate combination of keystrokes.</span></span>

- <span data-ttu-id="81b54-115">已啟動的控制項上會引發<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> (以回應執行相關動作的控制項)。</span><span class="sxs-lookup"><span data-stu-id="81b54-115"><xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> is raised on a control that has been activated (as a response to a control carrying out its associated action).</span></span> <span data-ttu-id="81b54-116">在可能的情況下，應該是在控制項完成該動作並返回，且沒有發生封鎖時才會引發該事件。</span><span class="sxs-lookup"><span data-stu-id="81b54-116">If possible, the event should be raised after the control has completed the action and returned without blocking.</span></span> <span data-ttu-id="81b54-117">在下列情節中，叫用事件應該在服務叫用要求之前引發：</span><span class="sxs-lookup"><span data-stu-id="81b54-117">The Invoked event should be raised before servicing the Invoke request in the following scenarios:</span></span>

  - <span data-ttu-id="81b54-118">無法或不適合等待至動作完成。</span><span class="sxs-lookup"><span data-stu-id="81b54-118">It is not possible or practical to wait until the action is complete.</span></span>

  - <span data-ttu-id="81b54-119">動作需要使用者互動。</span><span class="sxs-lookup"><span data-stu-id="81b54-119">The action requires user interaction.</span></span>

  - <span data-ttu-id="81b54-120">動作費時，且會導致發出呼叫的用戶端長時間凍結。</span><span class="sxs-lookup"><span data-stu-id="81b54-120">The action is time-consuming and will cause the calling client to block for a significant amount of time.</span></span>

- <span data-ttu-id="81b54-121">如果叫用控制項會有嚴重的副作用，就必須透過 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> 屬性公開這些副作用。</span><span class="sxs-lookup"><span data-stu-id="81b54-121">If invoking the control has significant side-effects, those side-effects should be exposed through the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> property.</span></span> <span data-ttu-id="81b54-122">例如，雖然 <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 和選取範圍沒有關聯，但 <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 卻可能會造成其他控制項受到選取。</span><span class="sxs-lookup"><span data-stu-id="81b54-122">For example, even though <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> is not associated with selection, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> may cause another control to become selected.</span></span>

- <span data-ttu-id="81b54-123">停留 (滑鼠在上) 效果通常不會形成叫用事件。</span><span class="sxs-lookup"><span data-stu-id="81b54-123">Hover (or mouse-over) effects generally do not constitute an Invoked event.</span></span> <span data-ttu-id="81b54-124">但是，根據停留狀態而執行動作 (相對於產生視覺效果) 的控制項，應該要支援 <xref:System.Windows.Automation.InvokePattern> 控制項模式。</span><span class="sxs-lookup"><span data-stu-id="81b54-124">However, controls that perform an action (as opposed to cause a visual effect) based on the hover state should support the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="81b54-125">如果控制項的叫用是與滑鼠相關的副作用所造成的，便會將這個實作視為協助工具問題。</span><span class="sxs-lookup"><span data-stu-id="81b54-125">This implementation is considered an accessibility issue if the control can be invoked only as a result of a mouse-related side effect.</span></span>

- <span data-ttu-id="81b54-126">叫用控制項和選擇項目不同。</span><span class="sxs-lookup"><span data-stu-id="81b54-126">Invoking a control is different from selecting an item.</span></span> <span data-ttu-id="81b54-127">但是，依據控制項而定，叫用某些控制項可能會有造成此項目受到選取的副作用。</span><span class="sxs-lookup"><span data-stu-id="81b54-127">However, depending on the control, invoking it may cause the item to become selected as a side-effect.</span></span> <span data-ttu-id="81b54-128">例如，叫用 [我的文件] 資料夾中的 Microsoft Word 檔案清單專案時，會選取該專案並開啟該檔。</span><span class="sxs-lookup"><span data-stu-id="81b54-128">For example, invoking a Microsoft Word document list item in the My Documents folder both selects the item and opens the document.</span></span>

- <span data-ttu-id="81b54-129">叫用某個項目時，此項目可能會立即從 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中消失。</span><span class="sxs-lookup"><span data-stu-id="81b54-129">An element can disappear from the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree immediately upon being invoked.</span></span> <span data-ttu-id="81b54-130">要求事件回呼所提供的項目資訊，可能會因此而失敗。</span><span class="sxs-lookup"><span data-stu-id="81b54-130">Requesting information from the element provided by the event callback may fail as a result.</span></span> <span data-ttu-id="81b54-131">建議的解決方法是預先擷取快取的資訊。</span><span class="sxs-lookup"><span data-stu-id="81b54-131">Pre-fetching cached information is the recommended workaround.</span></span>

- <span data-ttu-id="81b54-132">控制項可以實作多個控制項模式。</span><span class="sxs-lookup"><span data-stu-id="81b54-132">Controls can implement multiple control patterns.</span></span> <span data-ttu-id="81b54-133">例如，Microsoft Excel 工具列上的 [填滿色彩] 控制項會同時執行 [<xref:System.Windows.Automation.InvokePattern>] 和 [<xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式]。</span><span class="sxs-lookup"><span data-stu-id="81b54-133">For example, the Fill Color control on the Microsoft Excel toolbar implements both the <xref:System.Windows.Automation.InvokePattern> and the <xref:System.Windows.Automation.ExpandCollapsePattern> control patterns.</span></span> <span data-ttu-id="81b54-134"><xref:System.Windows.Automation.ExpandCollapsePattern> 會公開功能表，而 <xref:System.Windows.Automation.InvokePattern> 則會以選擇的色彩填滿作用中的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="81b54-134"><xref:System.Windows.Automation.ExpandCollapsePattern> exposes the menu and the <xref:System.Windows.Automation.InvokePattern> fills the active selection with the chosen color.</span></span>

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a><span data-ttu-id="81b54-135">IInvokeProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="81b54-135">Required Members for IInvokeProvider</span></span>

<span data-ttu-id="81b54-136">以下是實作 <xref:System.Windows.Automation.Provider.IInvokeProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="81b54-136">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IInvokeProvider>.</span></span>

|<span data-ttu-id="81b54-137">必要成員</span><span class="sxs-lookup"><span data-stu-id="81b54-137">Required members</span></span>|<span data-ttu-id="81b54-138">成員類型</span><span class="sxs-lookup"><span data-stu-id="81b54-138">Member type</span></span>|<span data-ttu-id="81b54-139">備註</span><span class="sxs-lookup"><span data-stu-id="81b54-139">Notes</span></span>|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|<span data-ttu-id="81b54-140">方法</span><span class="sxs-lookup"><span data-stu-id="81b54-140">method</span></span>|<span data-ttu-id="81b54-141"><xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 為非同步呼叫，且必須立即返回，不可封鎖。</span><span class="sxs-lookup"><span data-stu-id="81b54-141"><xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> is an asynchronous call and must return immediately without blocking.</span></span><br /><br /> <span data-ttu-id="81b54-142">對於叫用時直接或間接啟動強制回應對話方塊的控制項，此行為尤其重要。</span><span class="sxs-lookup"><span data-stu-id="81b54-142">This behavior is particularly critical for controls that, directly or indirectly, launch a modal dialog when invoked.</span></span> <span data-ttu-id="81b54-143">任何引發事件的使用者介面自動化用戶端都會維持封鎖的狀態，直到強制回應對話方塊關閉為止。</span><span class="sxs-lookup"><span data-stu-id="81b54-143">Any UI Automation client that instigated the event will remain blocked until the modal dialog is closed.</span></span>|

<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="81b54-144">例外狀況</span><span class="sxs-lookup"><span data-stu-id="81b54-144">Exceptions</span></span>

<span data-ttu-id="81b54-145">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="81b54-145">Providers must throw the following exceptions.</span></span>

|<span data-ttu-id="81b54-146">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="81b54-146">Exception Type</span></span>|<span data-ttu-id="81b54-147">條件</span><span class="sxs-lookup"><span data-stu-id="81b54-147">Condition</span></span>|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|<span data-ttu-id="81b54-148">如果未啟用此控制項。</span><span class="sxs-lookup"><span data-stu-id="81b54-148">If the control is not enabled.</span></span>|

## <a name="see-also"></a><span data-ttu-id="81b54-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="81b54-149">See also</span></span>

- [<span data-ttu-id="81b54-150">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="81b54-150">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="81b54-151">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="81b54-151">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="81b54-152">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="81b54-152">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="81b54-153">使用 UI 自動化叫用控制項</span><span class="sxs-lookup"><span data-stu-id="81b54-153">Invoke a Control Using UI Automation</span></span>](invoke-a-control-using-ui-automation.md)
- [<span data-ttu-id="81b54-154">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="81b54-154">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="81b54-155">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="81b54-155">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
