---
title: 實作 UI 自動化 TableItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 4374666ba5e03720413614c63b00ba987f81f58f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447090"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="627b6-102">實作 UI 自動化 TableItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="627b6-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="627b6-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="627b6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="627b6-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="627b6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="627b6-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.ITableItemProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="627b6-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="627b6-106">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="627b6-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="627b6-107"><xref:System.Windows.Automation.TableItemPattern> 控制項模式是用以支援實作 <xref:System.Windows.Automation.Provider.ITableProvider> 之容器的子控制項。</span><span class="sxs-lookup"><span data-stu-id="627b6-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="627b6-108">個別資料格功能的存取權由 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的必要並行實作提供。</span><span class="sxs-lookup"><span data-stu-id="627b6-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="627b6-109">此控制項模式相當於 <xref:System.Windows.Automation.Provider.IGridItemProvider>，差別在於任何實作 <xref:System.Windows.Automation.Provider.ITableItemProvider> 的控制項必須以程式設計方式公開個別資料格與其資料列和資料行資訊之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="627b6-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="627b6-110">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="627b6-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="627b6-111">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="627b6-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="627b6-112">如需相關的格線專案功能，請參閱[執行 UI 自動化 GridItem 控制項模式](implementing-the-ui-automation-griditem-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="627b6-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="627b6-113">ITableItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="627b6-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="627b6-114">必要成員</span><span class="sxs-lookup"><span data-stu-id="627b6-114">Required member</span></span>|<span data-ttu-id="627b6-115">成員類型</span><span class="sxs-lookup"><span data-stu-id="627b6-115">Member type</span></span>|<span data-ttu-id="627b6-116">注意事項</span><span class="sxs-lookup"><span data-stu-id="627b6-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="627b6-117">方法</span><span class="sxs-lookup"><span data-stu-id="627b6-117">Method</span></span>|<span data-ttu-id="627b6-118">無</span><span class="sxs-lookup"><span data-stu-id="627b6-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="627b6-119">方法</span><span class="sxs-lookup"><span data-stu-id="627b6-119">Method</span></span>|<span data-ttu-id="627b6-120">無</span><span class="sxs-lookup"><span data-stu-id="627b6-120">None</span></span>|  
  
 <span data-ttu-id="627b6-121">此控制項模式沒有任何相關聯的屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="627b6-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="627b6-122">例外狀況</span><span class="sxs-lookup"><span data-stu-id="627b6-122">Exceptions</span></span>  
 <span data-ttu-id="627b6-123">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="627b6-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="627b6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="627b6-124">See also</span></span>

- [<span data-ttu-id="627b6-125">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="627b6-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="627b6-126">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="627b6-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="627b6-127">UI Automation Control Patterns for Clients</span><span class="sxs-lookup"><span data-stu-id="627b6-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="627b6-128">實作 UI 自動化 Table 控制項模式</span><span class="sxs-lookup"><span data-stu-id="627b6-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="627b6-129">實作 UI 自動化 GridItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="627b6-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="627b6-130">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="627b6-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="627b6-131">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="627b6-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
