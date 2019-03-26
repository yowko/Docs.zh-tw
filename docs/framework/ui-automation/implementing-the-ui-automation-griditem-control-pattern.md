---
title: 實作 UI 自動化 GridItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: ff3f52d37a7d45b92981969983652f48f5071959
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675767"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="63e3c-102">實作 UI 自動化 GridItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="63e3c-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="63e3c-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="63e3c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="63e3c-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="63e3c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="63e3c-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IGridItemProvider>的方針和慣例，包括屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="63e3c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="63e3c-106">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="63e3c-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="63e3c-107"><xref:System.Windows.Automation.GridItemPattern> 控制項模式是用以支援實作 <xref:System.Windows.Automation.Provider.IGridProvider> 之容器的個別子控制項。</span><span class="sxs-lookup"><span data-stu-id="63e3c-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="63e3c-108">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="63e3c-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="63e3c-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="63e3c-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="63e3c-110">實作 <xref:System.Windows.Automation.Provider.IGridProvider> 時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="63e3c-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="63e3c-111">方格座標是以零起始，左上資料格座標為 (0, 0)。</span><span class="sxs-lookup"><span data-stu-id="63e3c-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="63e3c-112">合併的資料格將會根據其基礎的錨定儲存格 (如使用者介面自動化提供者所定義)，報告其 <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> 和 <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="63e3c-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="63e3c-113">通常，它會是最上層或最左邊的資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="63e3c-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
-   <span data-ttu-id="63e3c-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> 不提供方格的主動操作，例如合併或分割儲存格。</span><span class="sxs-lookup"><span data-stu-id="63e3c-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
-   <span data-ttu-id="63e3c-115">通常可以使用鍵盤周遊實作 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的控制項 (也就是，使用者介面自動化用戶端可以移到相鄰的控制項)。</span><span class="sxs-lookup"><span data-stu-id="63e3c-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="63e3c-116">IGridItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="63e3c-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="63e3c-117">以下是實作 <xref:System.Windows.Automation.Provider.IGridItemProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="63e3c-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="63e3c-118">必要成員</span><span class="sxs-lookup"><span data-stu-id="63e3c-118">Required members</span></span>|<span data-ttu-id="63e3c-119">成員類型</span><span class="sxs-lookup"><span data-stu-id="63e3c-119">Member type</span></span>|<span data-ttu-id="63e3c-120">注意</span><span class="sxs-lookup"><span data-stu-id="63e3c-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="63e3c-121">屬性</span><span class="sxs-lookup"><span data-stu-id="63e3c-121">Property</span></span>|<span data-ttu-id="63e3c-122">None</span><span class="sxs-lookup"><span data-stu-id="63e3c-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="63e3c-123">屬性</span><span class="sxs-lookup"><span data-stu-id="63e3c-123">Property</span></span>|<span data-ttu-id="63e3c-124">None</span><span class="sxs-lookup"><span data-stu-id="63e3c-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="63e3c-125">屬性</span><span class="sxs-lookup"><span data-stu-id="63e3c-125">Property</span></span>|<span data-ttu-id="63e3c-126">None</span><span class="sxs-lookup"><span data-stu-id="63e3c-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="63e3c-127">屬性</span><span class="sxs-lookup"><span data-stu-id="63e3c-127">Property</span></span>|<span data-ttu-id="63e3c-128">None</span><span class="sxs-lookup"><span data-stu-id="63e3c-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="63e3c-129">屬性</span><span class="sxs-lookup"><span data-stu-id="63e3c-129">Property</span></span>|<span data-ttu-id="63e3c-130">None</span><span class="sxs-lookup"><span data-stu-id="63e3c-130">None</span></span>|  
  
 <span data-ttu-id="63e3c-131">此控制項模式沒有任何相關聯的方法或事件。</span><span class="sxs-lookup"><span data-stu-id="63e3c-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="63e3c-132">例外狀況</span><span class="sxs-lookup"><span data-stu-id="63e3c-132">Exceptions</span></span>  
 <span data-ttu-id="63e3c-133">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63e3c-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e3c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63e3c-134">See also</span></span>
- [<span data-ttu-id="63e3c-135">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="63e3c-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="63e3c-136">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="63e3c-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="63e3c-137">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="63e3c-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="63e3c-138">實作 UI 自動化 Grid 控制項模式</span><span class="sxs-lookup"><span data-stu-id="63e3c-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="63e3c-139">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="63e3c-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="63e3c-140">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="63e3c-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
