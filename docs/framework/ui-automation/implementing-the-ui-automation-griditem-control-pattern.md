---
title: 實作 UI 自動化 GridItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 68de80e4a01de27c16c0ed85c4177c562d5e328b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089944"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="7a1f6-102">實作 UI 自動化 GridItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="7a1f6-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="7a1f6-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7a1f6-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7a1f6-105">本主題將介紹的實作方針和慣例<xref:System.Windows.Automation.Provider.IGridItemProvider>，包括內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="7a1f6-106">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="7a1f6-107"><xref:System.Windows.Automation.GridItemPattern>控制項模式用以支援實作容器的個別子控制項<xref:System.Windows.Automation.Provider.IGridProvider>。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="7a1f6-108">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7a1f6-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="7a1f6-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="7a1f6-110">當實作<xref:System.Windows.Automation.Provider.IGridProvider>，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="7a1f6-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="7a1f6-111">方格座標是以零起始，左上資料格座標為 (0, 0)。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="7a1f6-112">合併的資料格將會報告它們<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>和<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>屬性根據其基礎的錨定儲存格所定義的使用者介面自動化提供者。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="7a1f6-113">通常，它會是最上層或最左邊的資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
-   <span data-ttu-id="7a1f6-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> 不提供例如合併或分割資料格方格的主動操作。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
-   <span data-ttu-id="7a1f6-115">控制實作<xref:System.Windows.Automation.Provider.IGridItemProvider>通常可周遊 （也就是使用者介面自動化用戶端可以移至相鄰的控制項） 使用鍵盤。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="7a1f6-116">IGridItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="7a1f6-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="7a1f6-117">以下是實作 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="7a1f6-118">必要成員</span><span class="sxs-lookup"><span data-stu-id="7a1f6-118">Required members</span></span>|<span data-ttu-id="7a1f6-119">成員類型</span><span class="sxs-lookup"><span data-stu-id="7a1f6-119">Member type</span></span>|<span data-ttu-id="7a1f6-120">注意</span><span class="sxs-lookup"><span data-stu-id="7a1f6-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="7a1f6-121">屬性</span><span class="sxs-lookup"><span data-stu-id="7a1f6-121">Property</span></span>|<span data-ttu-id="7a1f6-122">無</span><span class="sxs-lookup"><span data-stu-id="7a1f6-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="7a1f6-123">屬性</span><span class="sxs-lookup"><span data-stu-id="7a1f6-123">Property</span></span>|<span data-ttu-id="7a1f6-124">無</span><span class="sxs-lookup"><span data-stu-id="7a1f6-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="7a1f6-125">屬性</span><span class="sxs-lookup"><span data-stu-id="7a1f6-125">Property</span></span>|<span data-ttu-id="7a1f6-126">無</span><span class="sxs-lookup"><span data-stu-id="7a1f6-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="7a1f6-127">屬性</span><span class="sxs-lookup"><span data-stu-id="7a1f6-127">Property</span></span>|<span data-ttu-id="7a1f6-128">無</span><span class="sxs-lookup"><span data-stu-id="7a1f6-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="7a1f6-129">屬性</span><span class="sxs-lookup"><span data-stu-id="7a1f6-129">Property</span></span>|<span data-ttu-id="7a1f6-130">無</span><span class="sxs-lookup"><span data-stu-id="7a1f6-130">None</span></span>|  
  
 <span data-ttu-id="7a1f6-131">此控制項模式沒有任何相關聯的方法或事件。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="7a1f6-132">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7a1f6-132">Exceptions</span></span>  
 <span data-ttu-id="7a1f6-133">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7a1f6-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1f6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a1f6-134">See Also</span></span>  
 [<span data-ttu-id="7a1f6-135">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="7a1f6-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="7a1f6-136">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="7a1f6-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="7a1f6-137">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="7a1f6-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="7a1f6-138">實作 UI 自動化 Grid 控制項模式</span><span class="sxs-lookup"><span data-stu-id="7a1f6-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="7a1f6-139">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="7a1f6-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="7a1f6-140">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="7a1f6-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
