---
title: "GroupBox 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99150de10fcbd45d3617621a916793ad5cfe72db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="03a73-102">GroupBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="03a73-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="03a73-103">本主題描述樣式和範本<xref:System.Windows.Controls.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="03a73-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="03a73-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="03a73-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="03a73-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="03a73-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="03a73-106">GroupBox 組件</span><span class="sxs-lookup"><span data-stu-id="03a73-106">GroupBox Parts</span></span>  
 <span data-ttu-id="03a73-107"><xref:System.Windows.Controls.GroupBox>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="03a73-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="03a73-108">GroupBox 狀態</span><span class="sxs-lookup"><span data-stu-id="03a73-108">GroupBox States</span></span>  
 <span data-ttu-id="03a73-109">下表列出的視覺狀態<xref:System.Windows.Controls.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="03a73-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="03a73-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="03a73-110">VisualState Name</span></span>|<span data-ttu-id="03a73-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="03a73-111">VisualStateGroup Name</span></span>|<span data-ttu-id="03a73-112">描述</span><span class="sxs-lookup"><span data-stu-id="03a73-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="03a73-113">驗證</span><span class="sxs-lookup"><span data-stu-id="03a73-113">Valid</span></span>|<span data-ttu-id="03a73-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="03a73-114">ValidationStates</span></span>|<span data-ttu-id="03a73-115">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="03a73-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="03a73-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="03a73-116">InvalidFocused</span></span>|<span data-ttu-id="03a73-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="03a73-117">ValidationStates</span></span>|<span data-ttu-id="03a73-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="03a73-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="03a73-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="03a73-119">InvalidUnfocused</span></span>|<span data-ttu-id="03a73-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="03a73-120">ValidationStates</span></span>|<span data-ttu-id="03a73-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="03a73-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="03a73-122">GroupBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="03a73-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="03a73-123">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="03a73-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="03a73-124"><xref:System.Windows.Controls.ControlTemplate>會使用一個或多個下列資源。</span><span class="sxs-lookup"><span data-stu-id="03a73-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="03a73-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="03a73-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a73-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="03a73-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="03a73-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="03a73-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="03a73-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="03a73-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="03a73-129">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="03a73-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="03a73-130">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="03a73-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
