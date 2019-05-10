---
title: 實作 UI 自動化 TableItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3893f69ca6f73665ea3ea4b4f07970b847097f11
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649461"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="9c0ea-102">實作 UI 自動化 TableItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="9c0ea-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="9c0ea-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9c0ea-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9c0ea-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.ITableItemProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="9c0ea-106">其他參考的連結會在概觀的結尾列出。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9c0ea-107"><xref:System.Windows.Automation.TableItemPattern> 控制項模式是用以支援實作 <xref:System.Windows.Automation.Provider.ITableProvider> 之容器的子控制項。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="9c0ea-108">個別資料格功能的存取權由 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的必要並行實作提供。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="9c0ea-109">此控制項模式相當於 <xref:System.Windows.Automation.Provider.IGridItemProvider>，差別在於任何實作 <xref:System.Windows.Automation.Provider.ITableItemProvider> 的控制項必須以程式設計方式公開個別資料格與其資料列和資料行資訊之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="9c0ea-110">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9c0ea-111">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="9c0ea-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="9c0ea-112">如需相關的格線項目功能，請參閱[實作 UI 自動化 GridItem 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="9c0ea-113">ITableItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="9c0ea-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="9c0ea-114">必要成員</span><span class="sxs-lookup"><span data-stu-id="9c0ea-114">Required member</span></span>|<span data-ttu-id="9c0ea-115">成員類型</span><span class="sxs-lookup"><span data-stu-id="9c0ea-115">Member type</span></span>|<span data-ttu-id="9c0ea-116">注意</span><span class="sxs-lookup"><span data-stu-id="9c0ea-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="9c0ea-117">方法</span><span class="sxs-lookup"><span data-stu-id="9c0ea-117">Method</span></span>|<span data-ttu-id="9c0ea-118">None</span><span class="sxs-lookup"><span data-stu-id="9c0ea-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="9c0ea-119">方法</span><span class="sxs-lookup"><span data-stu-id="9c0ea-119">Method</span></span>|<span data-ttu-id="9c0ea-120">None</span><span class="sxs-lookup"><span data-stu-id="9c0ea-120">None</span></span>|  
  
 <span data-ttu-id="9c0ea-121">此控制項模式沒有任何相關聯的屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="9c0ea-122">例外狀況</span><span class="sxs-lookup"><span data-stu-id="9c0ea-122">Exceptions</span></span>  
 <span data-ttu-id="9c0ea-123">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0ea-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c0ea-124">See also</span></span>

- [<span data-ttu-id="9c0ea-125">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="9c0ea-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9c0ea-126">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="9c0ea-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9c0ea-127">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="9c0ea-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9c0ea-128">實作 UI 自動化 Table 控制項模式</span><span class="sxs-lookup"><span data-stu-id="9c0ea-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="9c0ea-129">實作 UI 自動化 GridItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="9c0ea-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="9c0ea-130">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="9c0ea-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="9c0ea-131">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="9c0ea-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
