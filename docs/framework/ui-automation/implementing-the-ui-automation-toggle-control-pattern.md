---
title: 實作 UI 自動化 Toggle 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 75659182fae64c548fe67090b13d43a212e6abae
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679026"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="24b36-102">實作 UI 自動化 Toggle 控制項模式</span><span class="sxs-lookup"><span data-stu-id="24b36-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="24b36-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="24b36-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="24b36-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="24b36-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="24b36-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IToggleProvider>的方針和慣例，包括方法和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="24b36-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="24b36-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="24b36-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="24b36-107"><xref:System.Windows.Automation.TogglePattern> 控制項模式是用來支援可循環顯示一組狀態，並在設定之後維持狀態的控制項。</span><span class="sxs-lookup"><span data-stu-id="24b36-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="24b36-108">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="24b36-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="24b36-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="24b36-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="24b36-110">實作切換控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="24b36-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="24b36-111">若控制項在啟動後不會維持狀態，如按鈕、工具列按鈕和超連結，則必須改為實作 <xref:System.Windows.Automation.Provider.IInvokeProvider> 。</span><span class="sxs-lookup"><span data-stu-id="24b36-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
-   <span data-ttu-id="24b36-112">控制項必須以下列順序循環其 <xref:System.Windows.Automation.ToggleState> ： <xref:System.Windows.Automation.ToggleState.On>、 <xref:System.Windows.Automation.ToggleState.Off> 以及 <xref:System.Windows.Automation.ToggleState.Indeterminate>(若支援的話)。</span><span class="sxs-lookup"><span data-stu-id="24b36-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
-   <span data-ttu-id="24b36-113"><xref:System.Windows.Automation.TogglePattern> 不提供 SetState(newState) 方法，因為直接設定三種狀態的核取方塊，而不依適當的 <xref:System.Windows.Automation.ToggleState> 順序循環時會發生問題。</span><span class="sxs-lookup"><span data-stu-id="24b36-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
-   <span data-ttu-id="24b36-114">RadioButton 控制項不會實作 <xref:System.Windows.Automation.Provider.IToggleProvider>，因為它無法循環其有效狀態。</span><span class="sxs-lookup"><span data-stu-id="24b36-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="24b36-115">IToggleProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="24b36-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="24b36-116">以下是實作 <xref:System.Windows.Automation.Provider.IToggleProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="24b36-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="24b36-117">必要成員</span><span class="sxs-lookup"><span data-stu-id="24b36-117">Required member</span></span>|<span data-ttu-id="24b36-118">成員類型</span><span class="sxs-lookup"><span data-stu-id="24b36-118">Member type</span></span>|<span data-ttu-id="24b36-119">注意</span><span class="sxs-lookup"><span data-stu-id="24b36-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="24b36-120">方法</span><span class="sxs-lookup"><span data-stu-id="24b36-120">Method</span></span>|<span data-ttu-id="24b36-121">無</span><span class="sxs-lookup"><span data-stu-id="24b36-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="24b36-122">屬性</span><span class="sxs-lookup"><span data-stu-id="24b36-122">Property</span></span>|<span data-ttu-id="24b36-123">無</span><span class="sxs-lookup"><span data-stu-id="24b36-123">None</span></span>|  
  
 <span data-ttu-id="24b36-124">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="24b36-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="24b36-125">例外狀況</span><span class="sxs-lookup"><span data-stu-id="24b36-125">Exceptions</span></span>  
 <span data-ttu-id="24b36-126">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24b36-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b36-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24b36-127">See also</span></span>
- [<span data-ttu-id="24b36-128">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="24b36-128">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="24b36-129">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="24b36-129">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="24b36-130">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="24b36-130">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="24b36-131">使用 UI 自動化取得核取方塊的切換狀態</span><span class="sxs-lookup"><span data-stu-id="24b36-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="24b36-132">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="24b36-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="24b36-133">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="24b36-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
