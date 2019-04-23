---
title: HOW TO：對控制項套用 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 53d4984946143c15c4a2b71095529fb5ee7de4b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133545"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="d96fb-102">HOW TO：對控制項套用 FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="d96fb-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="d96fb-103">此範例將示範如何在資源建立焦點視覺化樣式，並套用樣式至控制項，使用<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d96fb-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d96fb-104">範例</span><span class="sxs-lookup"><span data-stu-id="d96fb-104">Example</span></span>  
 <span data-ttu-id="d96fb-105">下列範例會定義建立複合僅適用於該控制項鍵盤的焦點時的其他控制項的樣式[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d96fb-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="d96fb-106">這可以藉由定義的樣式<xref:System.Windows.Controls.ControlTemplate>，然後設定時，該樣式參考做為資源<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d96fb-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="d96fb-107">類似於框線外部矩形被位於外部的矩形區域。</span><span class="sxs-lookup"><span data-stu-id="d96fb-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="d96fb-108">調整大小樣式的修改，除非使用<xref:System.Windows.FrameworkElement.ActualHeight%2A>和<xref:System.Windows.FrameworkElement.ActualWidth%2A>套用焦點視覺化樣式的位置的矩形控制項。</span><span class="sxs-lookup"><span data-stu-id="d96fb-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="d96fb-109">此範例會設定為負數值<xref:System.Windows.FrameworkElement.Margin%2A>使稍微顯示取得焦點的控制項外框線。</span><span class="sxs-lookup"><span data-stu-id="d96fb-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="d96fb-110">A<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>會附加至任何隨附的控制項範本樣式從明確樣式或佈景主題樣式控制項的主要樣式可以仍會建立使用<xref:System.Windows.Controls.ControlTemplate>並將該樣式設定為<xref:System.Windows.FrameworkElement.Style%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d96fb-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="d96fb-111">焦點視覺化樣式應該一致地使用佈景主題或 UI，而不是使用每個可設定焦點的項目，另一種。</span><span class="sxs-lookup"><span data-stu-id="d96fb-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="d96fb-112">如需詳細資訊，請參閱 <<c0> [ 控制項和 FocusVisualStyle 中焦點的樣式](styling-for-focus-in-controls-and-focusvisualstyle.md)。</span><span class="sxs-lookup"><span data-stu-id="d96fb-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96fb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d96fb-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="d96fb-114">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="d96fb-114">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="d96fb-115">設定控制項中焦點的樣式和 FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="d96fb-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
