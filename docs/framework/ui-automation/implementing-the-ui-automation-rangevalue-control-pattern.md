---
title: 實作 UI 自動化 RangeValue 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3736d1e8b23b8e05882a3fe016be0ac1a18ef51d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877408"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="d11bd-102">實作 UI 自動化 RangeValue 控制項模式</span><span class="sxs-lookup"><span data-stu-id="d11bd-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="d11bd-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="d11bd-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d11bd-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="d11bd-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d11bd-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IRangeValueProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d11bd-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="d11bd-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="d11bd-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="d11bd-107"><xref:System.Windows.Automation.RangeValuePattern> 控制項模式用來支援可以設定為某範圍內的值之控制項。</span><span class="sxs-lookup"><span data-stu-id="d11bd-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="d11bd-108">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="d11bd-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d11bd-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="d11bd-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d11bd-110">實作範圍值控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="d11bd-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="d11bd-111">控制項可以根據地區設定或使用者偏好設定，重新劃分所支援屬性的刻度。</span><span class="sxs-lookup"><span data-stu-id="d11bd-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="d11bd-112">例如，溫度計控制項可以設為顯示華氏或攝氏溫度。</span><span class="sxs-lookup"><span data-stu-id="d11bd-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="d11bd-113">範圍值不明確的控制項 (如進度列或滑桿) 應將這些值正規化。</span><span class="sxs-lookup"><span data-stu-id="d11bd-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="d11bd-114">![進度列。](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="d11bd-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="d11bd-115">進度列範例，其中的值屬於整數類型，而最小值和最大值的屬性值分別正規化為 0 和 100。</span><span class="sxs-lookup"><span data-stu-id="d11bd-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="d11bd-116">IRangeValueProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="d11bd-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="d11bd-117">必要成員</span><span class="sxs-lookup"><span data-stu-id="d11bd-117">Required member</span></span>|<span data-ttu-id="d11bd-118">成員類型</span><span class="sxs-lookup"><span data-stu-id="d11bd-118">Member type</span></span>|<span data-ttu-id="d11bd-119">注意</span><span class="sxs-lookup"><span data-stu-id="d11bd-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="d11bd-120">屬性</span><span class="sxs-lookup"><span data-stu-id="d11bd-120">Property</span></span>|<span data-ttu-id="d11bd-121">無</span><span class="sxs-lookup"><span data-stu-id="d11bd-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="d11bd-122">屬性</span><span class="sxs-lookup"><span data-stu-id="d11bd-122">Property</span></span>|<span data-ttu-id="d11bd-123">無</span><span class="sxs-lookup"><span data-stu-id="d11bd-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="d11bd-124">屬性</span><span class="sxs-lookup"><span data-stu-id="d11bd-124">Property</span></span>|<span data-ttu-id="d11bd-125">無</span><span class="sxs-lookup"><span data-stu-id="d11bd-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="d11bd-126">屬性</span><span class="sxs-lookup"><span data-stu-id="d11bd-126">Property</span></span>|<span data-ttu-id="d11bd-127">無</span><span class="sxs-lookup"><span data-stu-id="d11bd-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="d11bd-128">屬性</span><span class="sxs-lookup"><span data-stu-id="d11bd-128">Property</span></span>|<span data-ttu-id="d11bd-129">無</span><span class="sxs-lookup"><span data-stu-id="d11bd-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="d11bd-130">屬性</span><span class="sxs-lookup"><span data-stu-id="d11bd-130">Property</span></span>|<span data-ttu-id="d11bd-131">無</span><span class="sxs-lookup"><span data-stu-id="d11bd-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="d11bd-132">方法</span><span class="sxs-lookup"><span data-stu-id="d11bd-132">Methods</span></span>|<span data-ttu-id="d11bd-133">無</span><span class="sxs-lookup"><span data-stu-id="d11bd-133">None</span></span>|  
  
 <span data-ttu-id="d11bd-134">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="d11bd-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d11bd-135">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d11bd-135">Exceptions</span></span>  
 <span data-ttu-id="d11bd-136">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d11bd-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="d11bd-137">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="d11bd-137">Exception type</span></span>|<span data-ttu-id="d11bd-138">條件</span><span class="sxs-lookup"><span data-stu-id="d11bd-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="d11bd-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> 以大於 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> 或小於 <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>的值呼叫。</span><span class="sxs-lookup"><span data-stu-id="d11bd-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d11bd-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d11bd-140">See Also</span></span>  
 [<span data-ttu-id="d11bd-141">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="d11bd-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="d11bd-142">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="d11bd-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="d11bd-143">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="d11bd-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="d11bd-144">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="d11bd-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="d11bd-145">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="d11bd-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
