---
title: 實作 UI 自動化 RangeValue 控制項模式
description: 請參閱在消費者介面自動化中執行 RangeValue 控制項模式的指導方針和慣例。 請參閱 System.windows.automation.provider.irangevalueprovider> 介面所需的成員。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 9b5bfd571b078b7aeab149f5371004ac832fadcc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239558"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="f30ac-104">實作 UI 自動化 RangeValue 控制項模式</span><span class="sxs-lookup"><span data-stu-id="f30ac-104">Implementing the UI Automation RangeValue Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="f30ac-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="f30ac-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f30ac-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="f30ac-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f30ac-107">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IRangeValueProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f30ac-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="f30ac-108">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="f30ac-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="f30ac-109"><xref:System.Windows.Automation.RangeValuePattern> 控制項模式用來支援可以設定為某範圍內的值之控制項。</span><span class="sxs-lookup"><span data-stu-id="f30ac-109">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="f30ac-110">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="f30ac-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="f30ac-111">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="f30ac-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="f30ac-112">實作範圍值控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="f30ac-112">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="f30ac-113">控制項可以根據地區設定或使用者偏好設定，重新劃分所支援屬性的刻度。</span><span class="sxs-lookup"><span data-stu-id="f30ac-113">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="f30ac-114">例如，溫度計控制項可以設為顯示華氏或攝氏溫度。</span><span class="sxs-lookup"><span data-stu-id="f30ac-114">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="f30ac-115">範圍值不明確的控制項 (如進度列或滑桿) 應將這些值正規化。</span><span class="sxs-lookup"><span data-stu-id="f30ac-115">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="f30ac-116">![進度列。](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="f30ac-116">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="f30ac-117">進度列範例，其中的值屬於整數類型，而最小值和最大值的屬性值分別正規化為 0 和 100。</span><span class="sxs-lookup"><span data-stu-id="f30ac-117">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>

## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="f30ac-118">IRangeValueProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="f30ac-118">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="f30ac-119">必要成員</span><span class="sxs-lookup"><span data-stu-id="f30ac-119">Required member</span></span>|<span data-ttu-id="f30ac-120">成員類型</span><span class="sxs-lookup"><span data-stu-id="f30ac-120">Member type</span></span>|<span data-ttu-id="f30ac-121">備註</span><span class="sxs-lookup"><span data-stu-id="f30ac-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="f30ac-122">屬性</span><span class="sxs-lookup"><span data-stu-id="f30ac-122">Property</span></span>|<span data-ttu-id="f30ac-123">無</span><span class="sxs-lookup"><span data-stu-id="f30ac-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="f30ac-124">屬性</span><span class="sxs-lookup"><span data-stu-id="f30ac-124">Property</span></span>|<span data-ttu-id="f30ac-125">無</span><span class="sxs-lookup"><span data-stu-id="f30ac-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="f30ac-126">屬性</span><span class="sxs-lookup"><span data-stu-id="f30ac-126">Property</span></span>|<span data-ttu-id="f30ac-127">無</span><span class="sxs-lookup"><span data-stu-id="f30ac-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="f30ac-128">屬性</span><span class="sxs-lookup"><span data-stu-id="f30ac-128">Property</span></span>|<span data-ttu-id="f30ac-129">無</span><span class="sxs-lookup"><span data-stu-id="f30ac-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="f30ac-130">屬性</span><span class="sxs-lookup"><span data-stu-id="f30ac-130">Property</span></span>|<span data-ttu-id="f30ac-131">無</span><span class="sxs-lookup"><span data-stu-id="f30ac-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="f30ac-132">屬性</span><span class="sxs-lookup"><span data-stu-id="f30ac-132">Property</span></span>|<span data-ttu-id="f30ac-133">無</span><span class="sxs-lookup"><span data-stu-id="f30ac-133">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="f30ac-134">方法</span><span class="sxs-lookup"><span data-stu-id="f30ac-134">Methods</span></span>|<span data-ttu-id="f30ac-135">無</span><span class="sxs-lookup"><span data-stu-id="f30ac-135">None</span></span>|  
  
 <span data-ttu-id="f30ac-136">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="f30ac-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="f30ac-137">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f30ac-137">Exceptions</span></span>  

 <span data-ttu-id="f30ac-138">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f30ac-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="f30ac-139">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="f30ac-139">Exception type</span></span>|<span data-ttu-id="f30ac-140">條件</span><span class="sxs-lookup"><span data-stu-id="f30ac-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="f30ac-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> 以大於 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> 或小於 <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>的值呼叫。</span><span class="sxs-lookup"><span data-stu-id="f30ac-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f30ac-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f30ac-142">See also</span></span>

- [<span data-ttu-id="f30ac-143">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="f30ac-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="f30ac-144">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="f30ac-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="f30ac-145">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="f30ac-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="f30ac-146">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="f30ac-146">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="f30ac-147">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="f30ac-147">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
