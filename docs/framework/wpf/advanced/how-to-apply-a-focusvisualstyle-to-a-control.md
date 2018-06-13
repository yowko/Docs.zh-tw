---
title: 如何：對控制項套用 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 34af5ca6f5ce6b3714d7d7e0d707841cdfc61349
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543728"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="f18c4-102">如何：對控制項套用 FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="f18c4-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="f18c4-103">此範例將示範如何建立資源中的焦點視覺化樣式，並套用樣式至控制項，使用<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f18c4-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18c4-104">範例</span><span class="sxs-lookup"><span data-stu-id="f18c4-104">Example</span></span>  
 <span data-ttu-id="f18c4-105">下列範例會定義建立複合只適用於該控制項時的焦點的鍵盤的其他控制項的樣式[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f18c4-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="f18c4-106">這會透過定義的樣式<xref:System.Windows.Controls.ControlTemplate>，然後設定時，該樣式參考做為資源<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f18c4-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="f18c4-107">類似框線外部矩形被位於外部的矩形區域。</span><span class="sxs-lookup"><span data-stu-id="f18c4-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="f18c4-108">調整大小樣式的修改，除非使用<xref:System.Windows.FrameworkElement.ActualHeight%2A>和<xref:System.Windows.FrameworkElement.ActualWidth%2A>的矩形的控制項焦點視覺化樣式套用的位置。</span><span class="sxs-lookup"><span data-stu-id="f18c4-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="f18c4-109">此範例會設定為負數值<xref:System.Windows.FrameworkElement.Margin%2A>使稍微顯示取得焦點的控制項外框線。</span><span class="sxs-lookup"><span data-stu-id="f18c4-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="f18c4-110">A<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>是附加至任何控制項範本樣式出現明確樣式或佈景主題樣式; 從主控制項的樣式可以仍會建立使用<xref:System.Windows.Controls.ControlTemplate>並將該樣式設定為<xref:System.Windows.FrameworkElement.Style%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f18c4-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="f18c4-111">焦點視覺樣式應該一致使用跨主題或 UI，而不是使用不同的另一個用於每個可設定焦點的項目。</span><span class="sxs-lookup"><span data-stu-id="f18c4-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="f18c4-112">如需詳細資訊，請參閱[樣式的焦點在控制項和 FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)。</span><span class="sxs-lookup"><span data-stu-id="f18c4-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18c4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f18c4-113">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [<span data-ttu-id="f18c4-114">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="f18c4-114">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f18c4-115">設定控制項中焦點的樣式和 FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="f18c4-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
