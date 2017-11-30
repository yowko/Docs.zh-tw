---
title: "Label 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 013d21c7547531541c89435dbbdde65911ae3750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="4b0cd-102">Label 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="4b0cd-102">Label Styles and Templates</span></span>
<span data-ttu-id="4b0cd-103">本主題描述樣式和範本<xref:System.Windows.Controls.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="4b0cd-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4b0cd-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="4b0cd-106">標籤部分</span><span class="sxs-lookup"><span data-stu-id="4b0cd-106">Label Parts</span></span>  
 <span data-ttu-id="4b0cd-107"><xref:System.Windows.Controls.Label>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="4b0cd-108">標籤狀態</span><span class="sxs-lookup"><span data-stu-id="4b0cd-108">Label States</span></span>  
 <span data-ttu-id="4b0cd-109">下表列出的視覺狀態<xref:System.Windows.Controls.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="4b0cd-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="4b0cd-110">VisualState Name</span></span>|<span data-ttu-id="4b0cd-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="4b0cd-111">VisualStateGroup Name</span></span>|<span data-ttu-id="4b0cd-112">描述</span><span class="sxs-lookup"><span data-stu-id="4b0cd-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4b0cd-113">驗證</span><span class="sxs-lookup"><span data-stu-id="4b0cd-113">Valid</span></span>|<span data-ttu-id="4b0cd-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b0cd-114">ValidationStates</span></span>|<span data-ttu-id="4b0cd-115">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4b0cd-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4b0cd-116">InvalidFocused</span></span>|<span data-ttu-id="4b0cd-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b0cd-117">ValidationStates</span></span>|<span data-ttu-id="4b0cd-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4b0cd-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4b0cd-119">InvalidUnfocused</span></span>|<span data-ttu-id="4b0cd-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b0cd-120">ValidationStates</span></span>|<span data-ttu-id="4b0cd-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="4b0cd-122">標籤 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="4b0cd-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="4b0cd-123">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="4b0cd-124"><xref:System.Windows.Controls.ControlTemplate>會使用一個或多個下列資源。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4b0cd-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="4b0cd-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0cd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b0cd-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="4b0cd-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="4b0cd-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="4b0cd-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="4b0cd-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="4b0cd-129">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="4b0cd-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="4b0cd-130">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="4b0cd-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
