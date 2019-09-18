---
title: 實作 UI 自動化 Grid 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 222f79934b183b836f74575cdcc611588b41ce2a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043438"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="82ebb-102">實作 UI 自動化 Grid 控制項模式</span><span class="sxs-lookup"><span data-stu-id="82ebb-102">Implementing the UI Automation Grid Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="82ebb-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="82ebb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="82ebb-104">如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。</span><span class="sxs-lookup"><span data-stu-id="82ebb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="82ebb-105">本主題簡介實作 <xref:System.Windows.Automation.Provider.IGridProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="82ebb-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="82ebb-106">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="82ebb-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="82ebb-107"><xref:System.Windows.Automation.GridPattern> 控制項模式是用以支援當作子項目集合的容器使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="82ebb-107">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="82ebb-108">此項目的子系必須實作 <xref:System.Windows.Automation.Provider.IGridItemProvider> ，並組合管理成資料列與資料行可周遊的二維邏輯座標系統。</span><span class="sxs-lookup"><span data-stu-id="82ebb-108">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="82ebb-109">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="82ebb-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="82ebb-110">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="82ebb-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="82ebb-111">實作方格控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="82ebb-111">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="82ebb-112">方格座標是從左上角 (或根據地區為右上儲存格) 以零為起始，座標為 (0, 0)。</span><span class="sxs-lookup"><span data-stu-id="82ebb-112">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="82ebb-113">如果儲存格是空的，仍必須傳回使用者介面自動化項目，才能支援該儲存格的 <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="82ebb-113">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="82ebb-114">當子項目在方格中的配置類似不完全陣列 (請參閱以下範例)，就可能發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="82ebb-114">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="82ebb-115">![Windows Explorer 視圖顯示不完全的版面配置。](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="82ebb-115">![Windows Explorer view showing ragged layout.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="82ebb-116">座標是空的方格控制項範例</span><span class="sxs-lookup"><span data-stu-id="82ebb-116">Example of a Grid Control with Empty Coordinates</span></span>  
  
- <span data-ttu-id="82ebb-117">單一項目的方格仍必須實作 <xref:System.Windows.Automation.Provider.IGridProvider> ，才能在邏輯上視為是方格。</span><span class="sxs-lookup"><span data-stu-id="82ebb-117">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="82ebb-118">方格中的子項目數為多少都沒關係。</span><span class="sxs-lookup"><span data-stu-id="82ebb-118">The number of child items in the grid is immaterial.</span></span>  
  
- <span data-ttu-id="82ebb-119">根據提供者實作而定，隱藏資料列和資料行可能會載入到 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構，因此會反映在 <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> 和 <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="82ebb-119">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="82ebb-120">如果隱藏資料列和資料行未載入，則應不會列入計數。</span><span class="sxs-lookup"><span data-stu-id="82ebb-120">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
- <span data-ttu-id="82ebb-121"><xref:System.Windows.Automation.Provider.IGridProvider> 不會啟用方格的使用中操作，而必須實作 <xref:System.Windows.Automation.Provider.ITransformProvider> 才能啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="82ebb-121"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
- <span data-ttu-id="82ebb-122">使用 <xref:System.Windows.Automation.StructureChangedEventHandler> 接聽方格的結構或配置變更，例如新增、移除或合併儲存格。</span><span class="sxs-lookup"><span data-stu-id="82ebb-122">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
- <span data-ttu-id="82ebb-123">使用 <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> 追蹤方格項目或儲存格的周遊情形。</span><span class="sxs-lookup"><span data-stu-id="82ebb-123">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a><span data-ttu-id="82ebb-124">IGridProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="82ebb-124">Required Members for IGridProvider</span></span>  
 <span data-ttu-id="82ebb-125">以下是實作 IGridProvider 介面的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="82ebb-125">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="82ebb-126">必要成員</span><span class="sxs-lookup"><span data-stu-id="82ebb-126">Required members</span></span>|<span data-ttu-id="82ebb-127">類型</span><span class="sxs-lookup"><span data-stu-id="82ebb-127">Type</span></span>|<span data-ttu-id="82ebb-128">注意</span><span class="sxs-lookup"><span data-stu-id="82ebb-128">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="82ebb-129">屬性</span><span class="sxs-lookup"><span data-stu-id="82ebb-129">Property</span></span>|<span data-ttu-id="82ebb-130">無</span><span class="sxs-lookup"><span data-stu-id="82ebb-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="82ebb-131">屬性</span><span class="sxs-lookup"><span data-stu-id="82ebb-131">Property</span></span>|<span data-ttu-id="82ebb-132">None</span><span class="sxs-lookup"><span data-stu-id="82ebb-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="82ebb-133">方法</span><span class="sxs-lookup"><span data-stu-id="82ebb-133">Method</span></span>|<span data-ttu-id="82ebb-134">None</span><span class="sxs-lookup"><span data-stu-id="82ebb-134">None</span></span>|  
  
 <span data-ttu-id="82ebb-135">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="82ebb-135">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="82ebb-136">例外狀況</span><span class="sxs-lookup"><span data-stu-id="82ebb-136">Exceptions</span></span>  
 <span data-ttu-id="82ebb-137">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="82ebb-137">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="82ebb-138">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="82ebb-138">Exception type</span></span>|<span data-ttu-id="82ebb-139">條件</span><span class="sxs-lookup"><span data-stu-id="82ebb-139">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="82ebb-140">-如果要求的資料列座標大於， <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>或資料行座標<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>大於。</span><span class="sxs-lookup"><span data-stu-id="82ebb-140">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="82ebb-141">-如果要求的資料列或資料行座標之一小於零。</span><span class="sxs-lookup"><span data-stu-id="82ebb-141">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82ebb-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82ebb-142">See also</span></span>

- [<span data-ttu-id="82ebb-143">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="82ebb-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="82ebb-144">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="82ebb-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="82ebb-145">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="82ebb-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="82ebb-146">實作 UI 自動化 GridItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="82ebb-146">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="82ebb-147">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="82ebb-147">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="82ebb-148">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="82ebb-148">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
