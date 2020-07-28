---
title: 實作 UI 自動化 Table 控制項模式
description: 請參閱指導方針和慣例，在使用者介面自動化中執行資料表控制項模式。 知道 ITableProvider 介面的必要成員。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168236"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="4cfed-104">實作 UI 自動化 Table 控制項模式</span><span class="sxs-lookup"><span data-stu-id="4cfed-104">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="4cfed-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="4cfed-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4cfed-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="4cfed-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4cfed-107">本主題簡介實作 <xref:System.Windows.Automation.Provider.ITableProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4cfed-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="4cfed-108">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="4cfed-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="4cfed-109"><xref:System.Windows.Automation.TablePattern> 控制項模式是用以支援當作子項目集合的容器使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="4cfed-109">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="4cfed-110">此項目的子系必須實作 <xref:System.Windows.Automation.Provider.ITableItemProvider> ，並組合管理成資料列與資料行可周遊的二維邏輯座標系統。</span><span class="sxs-lookup"><span data-stu-id="4cfed-110">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="4cfed-111">此控制項模式類似 <xref:System.Windows.Automation.Provider.IGridProvider>，相反地，任何實作 <xref:System.Windows.Automation.Provider.ITableProvider> 的控制項也必須公開每個子項目的資料行及 (或) 資料列標頭關聯性。</span><span class="sxs-lookup"><span data-stu-id="4cfed-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="4cfed-112">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="4cfed-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="4cfed-113">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="4cfed-113">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="4cfed-114">實作表格控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="4cfed-114">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="4cfed-115">透過二維邏輯座標系統或必要 <xref:System.Windows.Automation.Provider.IGridProvider> 並行實作所提供的陣列，才可存取個別資料格的內容。</span><span class="sxs-lookup"><span data-stu-id="4cfed-115">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="4cfed-116">資料行或資料列標頭可以包含在資料表物件中，也可以是與資料表物件建立關係的個別標頭物件。</span><span class="sxs-lookup"><span data-stu-id="4cfed-116">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="4cfed-117">資料行和資料列標頭可同時包含主要標頭和任何支援的標頭。</span><span class="sxs-lookup"><span data-stu-id="4cfed-117">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cfed-118">這個概念會在使用者已定義「名字」資料行的 Microsoft Excel 試算表中明顯出現。</span><span class="sxs-lookup"><span data-stu-id="4cfed-118">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="4cfed-119">此資料行現在有兩個標頭—使用者定義的「名字」標頭和應用程式指派給該資料行的英數字元指定。</span><span class="sxs-lookup"><span data-stu-id="4cfed-119">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="4cfed-120">如需相關格線功能，請參閱[執行 UI 自動化方格控制項模式](implementing-the-ui-automation-grid-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="4cfed-120">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="4cfed-121">![包含複雜標頭項目的資料表](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="4cfed-121">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="4cfed-122">具有複雜資料行標頭的資料表範例</span><span class="sxs-lookup"><span data-stu-id="4cfed-122">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="4cfed-123">![具有模稜兩可之 RowOrColumnMajor 屬性的資料表。](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="4cfed-123">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="4cfed-124">具有模稜兩可之 RowOrColumnMajor 屬性的資料表範例</span><span class="sxs-lookup"><span data-stu-id="4cfed-124">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="4cfed-125">ITableProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="4cfed-125">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="4cfed-126">ITableProvider 介面需要下列屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="4cfed-126">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="4cfed-127">必要成員</span><span class="sxs-lookup"><span data-stu-id="4cfed-127">Required members</span></span>|<span data-ttu-id="4cfed-128">成員類型</span><span class="sxs-lookup"><span data-stu-id="4cfed-128">Member type</span></span>|<span data-ttu-id="4cfed-129">注意</span><span class="sxs-lookup"><span data-stu-id="4cfed-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="4cfed-130">屬性</span><span class="sxs-lookup"><span data-stu-id="4cfed-130">Property</span></span>|<span data-ttu-id="4cfed-131">None</span><span class="sxs-lookup"><span data-stu-id="4cfed-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="4cfed-132">方法</span><span class="sxs-lookup"><span data-stu-id="4cfed-132">Method</span></span>|<span data-ttu-id="4cfed-133">None</span><span class="sxs-lookup"><span data-stu-id="4cfed-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="4cfed-134">方法</span><span class="sxs-lookup"><span data-stu-id="4cfed-134">Method</span></span>|<span data-ttu-id="4cfed-135">None</span><span class="sxs-lookup"><span data-stu-id="4cfed-135">None</span></span>|  
  
 <span data-ttu-id="4cfed-136">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="4cfed-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="4cfed-137">例外狀況</span><span class="sxs-lookup"><span data-stu-id="4cfed-137">Exceptions</span></span>  
 <span data-ttu-id="4cfed-138">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4cfed-138">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cfed-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cfed-139">See also</span></span>

- [<span data-ttu-id="4cfed-140">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="4cfed-140">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="4cfed-141">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="4cfed-141">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="4cfed-142">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="4cfed-142">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="4cfed-143">實作 UI 自動化 TableItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="4cfed-143">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="4cfed-144">實作 UI 自動化 Grid 控制項模式</span><span class="sxs-lookup"><span data-stu-id="4cfed-144">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="4cfed-145">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="4cfed-145">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="4cfed-146">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="4cfed-146">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
