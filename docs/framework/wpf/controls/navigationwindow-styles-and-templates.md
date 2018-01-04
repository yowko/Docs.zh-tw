---
title: "NavigationWindow 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b638d43fb59506572e2ccddd9da7188639bff279
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="5f7ef-102">NavigationWindow 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="5f7ef-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="5f7ef-103">本主題描述樣式和範本<xref:System.Windows.Navigation.NavigationWindow>控制項。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="5f7ef-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5f7ef-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="5f7ef-106">NavigationWindow 組件</span><span class="sxs-lookup"><span data-stu-id="5f7ef-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="5f7ef-107">下表列出的具名組件<xref:System.Windows.Navigation.NavigationWindow>控制項。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="5f7ef-108">組件</span><span class="sxs-lookup"><span data-stu-id="5f7ef-108">Part</span></span>|<span data-ttu-id="5f7ef-109">類型</span><span class="sxs-lookup"><span data-stu-id="5f7ef-109">Type</span></span>|<span data-ttu-id="5f7ef-110">描述</span><span class="sxs-lookup"><span data-stu-id="5f7ef-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5f7ef-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="5f7ef-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="5f7ef-112">內容區域。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="5f7ef-113">NavigationWindow 狀態</span><span class="sxs-lookup"><span data-stu-id="5f7ef-113">NavigationWindow States</span></span>  
 <span data-ttu-id="5f7ef-114">下表列出的視覺狀態<xref:System.Windows.Navigation.NavigationWindow>控制項。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="5f7ef-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="5f7ef-115">VisualState Name</span></span>|<span data-ttu-id="5f7ef-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="5f7ef-116">VisualStateGroup Name</span></span>|<span data-ttu-id="5f7ef-117">描述</span><span class="sxs-lookup"><span data-stu-id="5f7ef-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5f7ef-118">驗證</span><span class="sxs-lookup"><span data-stu-id="5f7ef-118">Valid</span></span>|<span data-ttu-id="5f7ef-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5f7ef-119">ValidationStates</span></span>|<span data-ttu-id="5f7ef-120">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5f7ef-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5f7ef-121">InvalidFocused</span></span>|<span data-ttu-id="5f7ef-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5f7ef-122">ValidationStates</span></span>|<span data-ttu-id="5f7ef-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5f7ef-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5f7ef-124">InvalidUnfocused</span></span>|<span data-ttu-id="5f7ef-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5f7ef-125">ValidationStates</span></span>|<span data-ttu-id="5f7ef-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="5f7ef-127">NavigationWindow ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="5f7ef-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="5f7ef-128">雖然此範例中包含的所有項目中所定義的<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Navigation.NavigationWindow>根據預設，特定的值應視為範例。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="5f7ef-129">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5f7ef-130">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="5f7ef-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7ef-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="5f7ef-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="5f7ef-132">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="5f7ef-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="5f7ef-133">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="5f7ef-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="5f7ef-134">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="5f7ef-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="5f7ef-135">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="5f7ef-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
