---
title: 實作 UI 自動化 GridItem 控制項模式
description: 瞭解在消費者介面自動化中為格線專案執行 GridItemPattern 控制項模式的指導方針和慣例。 請參閱必要的 IGridItemProvider 成員。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 30932e630c663aabb7d26302174785d44dc1c385
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267880"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="91920-104">實作 UI 自動化 GridItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="91920-104">Implementing the UI Automation GridItem Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="91920-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="91920-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="91920-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="91920-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="91920-107">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IGridItemProvider>的方針和慣例，包括屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91920-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="91920-108">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="91920-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="91920-109"><xref:System.Windows.Automation.GridItemPattern> 控制項模式是用以支援實作 <xref:System.Windows.Automation.Provider.IGridProvider> 之容器的個別子控制項。</span><span class="sxs-lookup"><span data-stu-id="91920-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="91920-110">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="91920-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="91920-111">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="91920-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="91920-112">實作 <xref:System.Windows.Automation.Provider.IGridProvider> 時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="91920-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="91920-113">方格座標是以零起始，左上資料格座標為 (0, 0)。</span><span class="sxs-lookup"><span data-stu-id="91920-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="91920-114">合併的資料格將會根據其基礎的錨定儲存格 (如使用者介面自動化提供者所定義)，報告其 <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> 和 <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="91920-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="91920-115">通常，它會是最上層或最左邊的資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="91920-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="91920-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> 不提供方格的主動操作，例如合併或分割儲存格。</span><span class="sxs-lookup"><span data-stu-id="91920-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="91920-117">通常可以使用鍵盤周遊實作 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的控制項 (也就是，使用者介面自動化用戶端可以移到相鄰的控制項)。</span><span class="sxs-lookup"><span data-stu-id="91920-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>

## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="91920-118">IGridItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="91920-118">Required Members for IGridItemProvider</span></span>  

 <span data-ttu-id="91920-119">以下是實作 <xref:System.Windows.Automation.Provider.IGridItemProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="91920-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="91920-120">必要成員</span><span class="sxs-lookup"><span data-stu-id="91920-120">Required members</span></span>|<span data-ttu-id="91920-121">成員類型</span><span class="sxs-lookup"><span data-stu-id="91920-121">Member type</span></span>|<span data-ttu-id="91920-122">備註</span><span class="sxs-lookup"><span data-stu-id="91920-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="91920-123">屬性</span><span class="sxs-lookup"><span data-stu-id="91920-123">Property</span></span>|<span data-ttu-id="91920-124">無</span><span class="sxs-lookup"><span data-stu-id="91920-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="91920-125">屬性</span><span class="sxs-lookup"><span data-stu-id="91920-125">Property</span></span>|<span data-ttu-id="91920-126">無</span><span class="sxs-lookup"><span data-stu-id="91920-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="91920-127">屬性</span><span class="sxs-lookup"><span data-stu-id="91920-127">Property</span></span>|<span data-ttu-id="91920-128">無</span><span class="sxs-lookup"><span data-stu-id="91920-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="91920-129">屬性</span><span class="sxs-lookup"><span data-stu-id="91920-129">Property</span></span>|<span data-ttu-id="91920-130">無</span><span class="sxs-lookup"><span data-stu-id="91920-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="91920-131">屬性</span><span class="sxs-lookup"><span data-stu-id="91920-131">Property</span></span>|<span data-ttu-id="91920-132">無</span><span class="sxs-lookup"><span data-stu-id="91920-132">None</span></span>|  
  
 <span data-ttu-id="91920-133">此控制項模式沒有任何相關聯的方法或事件。</span><span class="sxs-lookup"><span data-stu-id="91920-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="91920-134">例外狀況</span><span class="sxs-lookup"><span data-stu-id="91920-134">Exceptions</span></span>  

 <span data-ttu-id="91920-135">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91920-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91920-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91920-136">See also</span></span>

- [<span data-ttu-id="91920-137">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="91920-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="91920-138">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="91920-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="91920-139">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="91920-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="91920-140">實作 UI 自動化 Grid 控制項模式</span><span class="sxs-lookup"><span data-stu-id="91920-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="91920-141">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="91920-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="91920-142">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="91920-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
