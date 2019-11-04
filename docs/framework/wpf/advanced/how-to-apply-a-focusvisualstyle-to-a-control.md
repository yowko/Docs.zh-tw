---
title: 如何：對控制項套用 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459815"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="95efa-102">如何：對控制項套用 FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="95efa-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="95efa-103">這個範例會示範如何使用 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性，在資源中建立焦點視覺化樣式，並將樣式套用至控制項。</span><span class="sxs-lookup"><span data-stu-id="95efa-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95efa-104">範例</span><span class="sxs-lookup"><span data-stu-id="95efa-104">Example</span></span>  
 <span data-ttu-id="95efa-105">下列範例定義的樣式會建立額外的控制群組合，只有在該控制項是 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]的鍵盤焦點時才適用。</span><span class="sxs-lookup"><span data-stu-id="95efa-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="95efa-106">這是藉由定義具有 <xref:System.Windows.Controls.ControlTemplate>的樣式來完成，然後在設定 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性時將該樣式參考為資源。</span><span class="sxs-lookup"><span data-stu-id="95efa-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="95efa-107">類似框線的外部矩形會放在矩形區域之外。</span><span class="sxs-lookup"><span data-stu-id="95efa-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="95efa-108">除非另有修改，否則樣式的大小會使用套用焦點視覺化樣式之矩形控制項的 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 和 <xref:System.Windows.FrameworkElement.ActualWidth%2A>。</span><span class="sxs-lookup"><span data-stu-id="95efa-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="95efa-109">這個範例會設定 <xref:System.Windows.FrameworkElement.Margin%2A> 的負值，讓框線在焦點的控制項之外稍微出現。</span><span class="sxs-lookup"><span data-stu-id="95efa-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="95efa-110"><xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 會加到任何來自明確樣式或主題樣式的控制項範本樣式;控制項的主要樣式仍然可以使用 <xref:System.Windows.Controls.ControlTemplate> 來建立，並將該樣式設定為 <xref:System.Windows.FrameworkElement.Style%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="95efa-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="95efa-111">焦點視覺化樣式應在主題或 UI 中一致地使用，而不是針對每個可設定焦點的元素使用不同的視覺效果樣式。</span><span class="sxs-lookup"><span data-stu-id="95efa-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="95efa-112">如需詳細資訊，請參閱將[焦點放在控制項中的樣式，以及 FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)。</span><span class="sxs-lookup"><span data-stu-id="95efa-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95efa-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="95efa-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="95efa-114">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="95efa-114">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="95efa-115">設定控制項中焦點的樣式和 FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="95efa-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
