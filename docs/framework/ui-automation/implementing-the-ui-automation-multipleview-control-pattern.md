---
title: 實作 UI 自動化 MultipleView 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 74e5908dfcd42d031464ffccedb530be4a71a3f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125194"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="024cc-102">實作 UI 自動化 MultipleView 控制項模式</span><span class="sxs-lookup"><span data-stu-id="024cc-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="024cc-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="024cc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="024cc-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="024cc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="024cc-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IMultipleViewProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="024cc-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="024cc-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="024cc-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="024cc-107"><xref:System.Windows.Automation.MultipleViewPattern> 控制項模式可用來支援控制項，這種控制項提供相同一組資訊或子控制項的多種不同表示，而且能夠在這些表示之間切換。</span><span class="sxs-lookup"><span data-stu-id="024cc-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="024cc-108">能夠呈現多種檢視的控制項包括清單檢視 (以縮圖、並排顯示、圖示或詳細資料顯示內容)、 [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] 圖表 (圓形圖、折線圖、橫條圖、含公式的儲存格值)、 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 文件 (標準、Web 版面配置、整頁模式、閱讀版面配置、大綱)、 [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] 行事曆 (年、月、星期、天) 以及 [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] 面板。</span><span class="sxs-lookup"><span data-stu-id="024cc-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="024cc-109">支援哪些檢視會由控制項的開發人員決定，而且是每個控制項所特有。</span><span class="sxs-lookup"><span data-stu-id="024cc-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="024cc-110">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="024cc-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="024cc-111">實作多重檢視控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="024cc-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="024cc-112">若管理目前檢視的容器與提供目前檢視的控制項不同，則也應在容器上實作<xref:System.Windows.Automation.Provider.IMultipleViewProvider> 。</span><span class="sxs-lookup"><span data-stu-id="024cc-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="024cc-113">例如，Windows 檔案總管包含目前資料夾內容的清單控制項，而控制項的檢視則是由 Windows 檔案總管應用程式管理。</span><span class="sxs-lookup"><span data-stu-id="024cc-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="024cc-114">可以排序內容的控制項不視為支援多種檢視。</span><span class="sxs-lookup"><span data-stu-id="024cc-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="024cc-115">檢視集合在執行個體之間必須完全相同。</span><span class="sxs-lookup"><span data-stu-id="024cc-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="024cc-116">檢視名稱必須適用於文字轉換語音、點字以及其他人類看得懂的應用程式。</span><span class="sxs-lookup"><span data-stu-id="024cc-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="024cc-117">IMultipleViewProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="024cc-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="024cc-118">以下是實作 IMultipleViewProvider 的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="024cc-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="024cc-119">必要成員</span><span class="sxs-lookup"><span data-stu-id="024cc-119">Required members</span></span>|<span data-ttu-id="024cc-120">成員類型</span><span class="sxs-lookup"><span data-stu-id="024cc-120">Member type</span></span>|<span data-ttu-id="024cc-121">注意</span><span class="sxs-lookup"><span data-stu-id="024cc-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="024cc-122">屬性</span><span class="sxs-lookup"><span data-stu-id="024cc-122">Property</span></span>|<span data-ttu-id="024cc-123">None</span><span class="sxs-lookup"><span data-stu-id="024cc-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="024cc-124">方法</span><span class="sxs-lookup"><span data-stu-id="024cc-124">Method</span></span>|<span data-ttu-id="024cc-125">None</span><span class="sxs-lookup"><span data-stu-id="024cc-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="024cc-126">方法</span><span class="sxs-lookup"><span data-stu-id="024cc-126">Method</span></span>|<span data-ttu-id="024cc-127">None</span><span class="sxs-lookup"><span data-stu-id="024cc-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="024cc-128">方法</span><span class="sxs-lookup"><span data-stu-id="024cc-128">Method</span></span>|<span data-ttu-id="024cc-129">None</span><span class="sxs-lookup"><span data-stu-id="024cc-129">None</span></span>|  
  
 <span data-ttu-id="024cc-130">這個控制項模式沒有相關事件。</span><span class="sxs-lookup"><span data-stu-id="024cc-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="024cc-131">例外狀況</span><span class="sxs-lookup"><span data-stu-id="024cc-131">Exceptions</span></span>  
 <span data-ttu-id="024cc-132">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="024cc-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="024cc-133">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="024cc-133">Exception type</span></span>|<span data-ttu-id="024cc-134">條件</span><span class="sxs-lookup"><span data-stu-id="024cc-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="024cc-135">呼叫 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> 或 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> 時使用的參數不是所支援檢視集合的成員。</span><span class="sxs-lookup"><span data-stu-id="024cc-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="024cc-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="024cc-136">See also</span></span>

- [<span data-ttu-id="024cc-137">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="024cc-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="024cc-138">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="024cc-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="024cc-139">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="024cc-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="024cc-140">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="024cc-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="024cc-141">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="024cc-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
