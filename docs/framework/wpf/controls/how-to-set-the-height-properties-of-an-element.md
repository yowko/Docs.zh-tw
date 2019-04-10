---
title: HOW TO：設定元素的高度屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: fb655630336c3b69afdc726a2e3c5a2cb8838667
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221583"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="31a9b-102">HOW TO：設定元素的高度屬性</span><span class="sxs-lookup"><span data-stu-id="31a9b-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="31a9b-103">範例</span><span class="sxs-lookup"><span data-stu-id="31a9b-103">Example</span></span>  
 <span data-ttu-id="31a9b-104">此範例中以視覺化方式顯示轉譯行為中的四個高度相關屬性之間的差異[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31a9b-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="31a9b-105"><xref:System.Windows.FrameworkElement>類別會公開四個屬性描述項目的高度特性。</span><span class="sxs-lookup"><span data-stu-id="31a9b-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="31a9b-106">這四個屬性可能會發生衝突，並會優先使用值時，請以下列方式決定：<xref:System.Windows.FrameworkElement.MinHeight%2A>值會優先於<xref:System.Windows.FrameworkElement.MaxHeight%2A>值，接著會優先於<xref:System.Windows.FrameworkElement.Height%2A>值。</span><span class="sxs-lookup"><span data-stu-id="31a9b-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="31a9b-107">第四個屬性，<xref:System.Windows.FrameworkElement.ActualHeight%2A>是唯讀的且會報告所決定的版面配置程序互動的實際高度。</span><span class="sxs-lookup"><span data-stu-id="31a9b-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="31a9b-108">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例繪製<xref:System.Windows.Shapes.Rectangle>項目 (`rect1`) 做為子系的<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="31a9b-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="31a9b-109">您可以變更目的高度屬性<xref:System.Windows.Shapes.Rectangle>使用的一系列<xref:System.Windows.Controls.ListBox>代表的屬性值的項目<xref:System.Windows.FrameworkElement.MinHeight%2A>， <xref:System.Windows.FrameworkElement.MaxHeight%2A>，和<xref:System.Windows.FrameworkElement.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="31a9b-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="31a9b-110">以這種方式，以視覺化方式顯示每個屬性的優先順序。</span><span class="sxs-lookup"><span data-stu-id="31a9b-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="31a9b-111">下列程式碼後置範例處理事件，<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件所引發。</span><span class="sxs-lookup"><span data-stu-id="31a9b-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="31a9b-112">每個處理常式會從輸入<xref:System.Windows.Controls.ListBox>，將做為值剖析<xref:System.Double>，並套用至指定的高度相關屬性的值。</span><span class="sxs-lookup"><span data-stu-id="31a9b-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="31a9b-113">高度值也會在轉換成字串，並寫入至各種<xref:System.Windows.Controls.TextBlock>（定義這些項目未顯示在 選取的 XAML） 的項目。</span><span class="sxs-lookup"><span data-stu-id="31a9b-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="31a9b-114">如需完整的範例，請參閱[高度屬性範例](https://go.microsoft.com/fwlink/?LinkID=159993)。</span><span class="sxs-lookup"><span data-stu-id="31a9b-114">For the complete sample, see [Height Properties Sample](https://go.microsoft.com/fwlink/?LinkID=159993).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a9b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31a9b-115">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="31a9b-116">設定元素的寬度屬性</span><span class="sxs-lookup"><span data-stu-id="31a9b-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="31a9b-117">面板概觀</span><span class="sxs-lookup"><span data-stu-id="31a9b-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="31a9b-118">高度屬性範例</span><span class="sxs-lookup"><span data-stu-id="31a9b-118">Height Properties Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159993)
