---
title: NavigationWindow 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 4aae14299b3959e7d2122991954cc62505d2a19e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460198"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="ce6a1-102">NavigationWindow 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ce6a1-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="ce6a1-103">本主題描述 <xref:System.Windows.Navigation.NavigationWindow> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="ce6a1-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ce6a1-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="ce6a1-106">NavigationWindow 元件</span><span class="sxs-lookup"><span data-stu-id="ce6a1-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="ce6a1-107">下表列出 <xref:System.Windows.Navigation.NavigationWindow> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="ce6a1-108">組件</span><span class="sxs-lookup"><span data-stu-id="ce6a1-108">Part</span></span>|<span data-ttu-id="ce6a1-109">輸入</span><span class="sxs-lookup"><span data-stu-id="ce6a1-109">Type</span></span>|<span data-ttu-id="ce6a1-110">描述</span><span class="sxs-lookup"><span data-stu-id="ce6a1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ce6a1-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="ce6a1-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="ce6a1-112">內容的區域。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="ce6a1-113">NavigationWindow 狀態</span><span class="sxs-lookup"><span data-stu-id="ce6a1-113">NavigationWindow States</span></span>  
 <span data-ttu-id="ce6a1-114">下表列出 <xref:System.Windows.Navigation.NavigationWindow> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="ce6a1-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ce6a1-115">VisualState Name</span></span>|<span data-ttu-id="ce6a1-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ce6a1-116">VisualStateGroup Name</span></span>|<span data-ttu-id="ce6a1-117">描述</span><span class="sxs-lookup"><span data-stu-id="ce6a1-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ce6a1-118">驗證</span><span class="sxs-lookup"><span data-stu-id="ce6a1-118">Valid</span></span>|<span data-ttu-id="ce6a1-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce6a1-119">ValidationStates</span></span>|<span data-ttu-id="ce6a1-120">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ce6a1-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ce6a1-121">InvalidFocused</span></span>|<span data-ttu-id="ce6a1-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce6a1-122">ValidationStates</span></span>|<span data-ttu-id="ce6a1-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ce6a1-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ce6a1-124">InvalidUnfocused</span></span>|<span data-ttu-id="ce6a1-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce6a1-125">ValidationStates</span></span>|<span data-ttu-id="ce6a1-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="ce6a1-127">NavigationWindow ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="ce6a1-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="ce6a1-128">雖然此範例包含預設會在 <xref:System.Windows.Navigation.NavigationWindow> 的 <xref:System.Windows.Controls.ControlTemplate> 中定義的所有元素，但應該將特定的值視為範例。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="ce6a1-129">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ce6a1-130">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="ce6a1-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6a1-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce6a1-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ce6a1-132">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ce6a1-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ce6a1-133">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="ce6a1-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ce6a1-134">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ce6a1-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ce6a1-135">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ce6a1-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
