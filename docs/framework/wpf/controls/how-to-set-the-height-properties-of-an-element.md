---
title: 如何：設定項目的高度屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124282"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="64cfc-102">如何：設定項目的高度屬性</span><span class="sxs-lookup"><span data-stu-id="64cfc-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="64cfc-103">範例</span><span class="sxs-lookup"><span data-stu-id="64cfc-103">Example</span></span>  
 <span data-ttu-id="64cfc-104">這個範例會以視覺化方式顯示 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中四個高度相關屬性之間的呈現行為差異。</span><span class="sxs-lookup"><span data-stu-id="64cfc-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="64cfc-105"><xref:System.Windows.FrameworkElement> 類別會公開四個屬性，以描述元素的高度特性。</span><span class="sxs-lookup"><span data-stu-id="64cfc-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="64cfc-106">這四個屬性可能會互相衝突，而當它們發生時，優先順序的值會決定如下： <xref:System.Windows.FrameworkElement.MinHeight%2A> 值優先于 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 值，而後者的優先順序高於 <xref:System.Windows.FrameworkElement.Height%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="64cfc-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="64cfc-107">第四個屬性（<xref:System.Windows.FrameworkElement.ActualHeight%2A>）是唯讀的，而且會回報與配置處理常式互動所決定的實際高度。</span><span class="sxs-lookup"><span data-stu-id="64cfc-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="64cfc-108">下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會將 <xref:System.Windows.Shapes.Rectangle> 元素（`rect1`）繪製為 <xref:System.Windows.Controls.Canvas>的子系。</span><span class="sxs-lookup"><span data-stu-id="64cfc-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="64cfc-109">您可以使用一系列的 <xref:System.Windows.Controls.ListBox> 元素來變更 <xref:System.Windows.Shapes.Rectangle> 的 height 屬性，這些專案代表 <xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>和 <xref:System.Windows.FrameworkElement.Height%2A>的屬性值。</span><span class="sxs-lookup"><span data-stu-id="64cfc-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="64cfc-110">如此一來，就會以視覺化方式顯示每個屬性的優先順序。</span><span class="sxs-lookup"><span data-stu-id="64cfc-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="64cfc-111">下列程式碼後置範例會處理 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件引發的事件。</span><span class="sxs-lookup"><span data-stu-id="64cfc-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="64cfc-112">每個處理常式都會接受來自 <xref:System.Windows.Controls.ListBox>的輸入、將值剖析為 <xref:System.Double>，並將值套用至指定的高度相關屬性。</span><span class="sxs-lookup"><span data-stu-id="64cfc-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="64cfc-113">高度值也會轉換為字串，並寫入至各種 <xref:System.Windows.Controls.TextBlock> 專案（這些元素的定義不會顯示在選取的 XAML 中）。</span><span class="sxs-lookup"><span data-stu-id="64cfc-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="64cfc-114">如需完整範例，請參閱[Height Properties sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)。</span><span class="sxs-lookup"><span data-stu-id="64cfc-114">For the complete sample, see [Height Properties Sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64cfc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64cfc-115">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="64cfc-116">設定元素的寬度屬性</span><span class="sxs-lookup"><span data-stu-id="64cfc-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="64cfc-117">面板概觀</span><span class="sxs-lookup"><span data-stu-id="64cfc-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="64cfc-118">Height 屬性範例</span><span class="sxs-lookup"><span data-stu-id="64cfc-118">Height Properties Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
