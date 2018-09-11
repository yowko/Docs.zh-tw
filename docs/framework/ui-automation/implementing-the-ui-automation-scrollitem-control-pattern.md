---
title: 實作 UI 自動化 ScrollItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0346b70b4400c5f7a8d282d945e029701973dad1
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272289"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="b448b-102">實作 UI 自動化 ScrollItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="b448b-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="b448b-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="b448b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b448b-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="b448b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b448b-105">本主題將介紹的實作方針和慣例<xref:System.Windows.Automation.Provider.IScrollItemProvider>，包括屬性、 方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b448b-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="b448b-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="b448b-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b448b-107"><xref:System.Windows.Automation.ScrollItemPattern>控制項模式用以支援實作容器的個別子控制項<xref:System.Windows.Automation.Provider.IScrollProvider>。</span><span class="sxs-lookup"><span data-stu-id="b448b-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="b448b-108">此控制項模式會擔任子控制項及其容器之間的通訊通道，以確保容器可變更其顯示子控制項的檢視區內目前可見內容 (或區域)。</span><span class="sxs-lookup"><span data-stu-id="b448b-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="b448b-109">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="b448b-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b448b-110">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="b448b-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b448b-111">實作捲軸項目控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="b448b-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="b448b-112">視窗或畫布控制項內含的項目不必實作 IScrollItemProvider 介面。</span><span class="sxs-lookup"><span data-stu-id="b448b-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="b448b-113">另外，不過，它們必須公開 （expose) 的有效位置<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>。</span><span class="sxs-lookup"><span data-stu-id="b448b-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="b448b-114">這可讓使用者介面自動化用戶端應用程式，使用<xref:System.Windows.Automation.ScrollPattern>控制項模式方法來顯示子項目的容器。</span><span class="sxs-lookup"><span data-stu-id="b448b-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="b448b-115">IScrollItemProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="b448b-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="b448b-116">實作 IScrollProvider 介面需要下列方法。</span><span class="sxs-lookup"><span data-stu-id="b448b-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="b448b-117">必要成員</span><span class="sxs-lookup"><span data-stu-id="b448b-117">Required members</span></span>|<span data-ttu-id="b448b-118">成員類型</span><span class="sxs-lookup"><span data-stu-id="b448b-118">Member type</span></span>|<span data-ttu-id="b448b-119">注意</span><span class="sxs-lookup"><span data-stu-id="b448b-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="b448b-120">方法</span><span class="sxs-lookup"><span data-stu-id="b448b-120">-   Method</span></span>|<span data-ttu-id="b448b-121">無</span><span class="sxs-lookup"><span data-stu-id="b448b-121">None</span></span>|  
  
 <span data-ttu-id="b448b-122">此控制項模式沒有任何相關聯的屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="b448b-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b448b-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b448b-123">Exceptions</span></span>  
 <span data-ttu-id="b448b-124">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b448b-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b448b-125">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="b448b-125">Exception Type</span></span>|<span data-ttu-id="b448b-126">條件</span><span class="sxs-lookup"><span data-stu-id="b448b-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="b448b-127">如果無法將項目捲動到檢視中：</span><span class="sxs-lookup"><span data-stu-id="b448b-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="b448b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b448b-128">See Also</span></span>  
 [<span data-ttu-id="b448b-129">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="b448b-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="b448b-130">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="b448b-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="b448b-131">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="b448b-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="b448b-132">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="b448b-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="b448b-133">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="b448b-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
