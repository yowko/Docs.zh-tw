---
title: Window 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: ebd21829591b8fefe87aeba0b86280f18eff4f06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203726"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="9427f-102">Window 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="9427f-102">Window Styles and Templates</span></span>
<span data-ttu-id="9427f-103">本主題描述的樣式和範本<xref:System.Windows.Window>控制項。</span><span class="sxs-lookup"><span data-stu-id="9427f-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="9427f-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="9427f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9427f-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="9427f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="9427f-106">視窗組件</span><span class="sxs-lookup"><span data-stu-id="9427f-106">Window Parts</span></span>  
 <span data-ttu-id="9427f-107"><xref:System.Windows.Window>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="9427f-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="9427f-108">視窗狀態</span><span class="sxs-lookup"><span data-stu-id="9427f-108">Window States</span></span>  
 <span data-ttu-id="9427f-109">下表列出的視覺狀態<xref:System.Windows.Window>控制項。</span><span class="sxs-lookup"><span data-stu-id="9427f-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="9427f-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="9427f-110">VisualState Name</span></span>|<span data-ttu-id="9427f-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="9427f-111">VisualStateGroup Name</span></span>|<span data-ttu-id="9427f-112">描述</span><span class="sxs-lookup"><span data-stu-id="9427f-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9427f-113">驗證</span><span class="sxs-lookup"><span data-stu-id="9427f-113">Valid</span></span>|<span data-ttu-id="9427f-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9427f-114">ValidationStates</span></span>|<span data-ttu-id="9427f-115">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="9427f-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9427f-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9427f-116">InvalidFocused</span></span>|<span data-ttu-id="9427f-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9427f-117">ValidationStates</span></span>|<span data-ttu-id="9427f-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="9427f-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9427f-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9427f-119">InvalidUnfocused</span></span>|<span data-ttu-id="9427f-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9427f-120">ValidationStates</span></span>|<span data-ttu-id="9427f-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="9427f-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="9427f-122">視窗的 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="9427f-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="9427f-123">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Window>控制項。</span><span class="sxs-lookup"><span data-stu-id="9427f-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="9427f-124"><xref:System.Windows.Controls.ControlTemplate>會使用一個或多個下列資源。</span><span class="sxs-lookup"><span data-stu-id="9427f-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9427f-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="9427f-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9427f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9427f-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9427f-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="9427f-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9427f-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="9427f-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9427f-129">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="9427f-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="9427f-130">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="9427f-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
