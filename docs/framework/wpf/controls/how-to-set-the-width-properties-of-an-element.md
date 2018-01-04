---
title: "如何：設定項目的寬度屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b27eb8f12e10f98d585f8f9bc445dba0118988fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="c9965-102">如何：設定項目的寬度屬性</span><span class="sxs-lookup"><span data-stu-id="c9965-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="c9965-103">範例</span><span class="sxs-lookup"><span data-stu-id="c9965-103">Example</span></span>  
 <span data-ttu-id="c9965-104">此範例以視覺化方式顯示在轉譯中的四個寬度相關屬性之間的行為差異[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c9965-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="c9965-105"><xref:System.Windows.FrameworkElement>類別會公開的四個屬性描述項目的寬度特性。</span><span class="sxs-lookup"><span data-stu-id="c9965-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="c9965-106">這四個屬性可能會發生衝突，並會優先使用的值時，請決定，如下所示：<xref:System.Windows.FrameworkElement.MinWidth%2A>值優先順序高於<xref:System.Windows.FrameworkElement.MaxWidth%2A>值接著會優先於<xref:System.Windows.FrameworkElement.Width%2A>值。</span><span class="sxs-lookup"><span data-stu-id="c9965-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="c9965-107">第四個屬性， <xref:System.Windows.FrameworkElement.ActualWidth%2A>、 處於唯讀狀態，和報表的版面配置處理序之間的互動所決定的實際寬度。</span><span class="sxs-lookup"><span data-stu-id="c9965-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="c9965-108">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例繪製<xref:System.Windows.Shapes.Rectangle>元素 (`rect1`) 做為子系<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="c9965-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="c9965-109">您可以變更的寬度屬性<xref:System.Windows.Shapes.Rectangle>使用一系列的<xref:System.Windows.Controls.ListBox>代表的屬性值的項目<xref:System.Windows.FrameworkElement.MinWidth%2A>， <xref:System.Windows.FrameworkElement.MaxWidth%2A>，和<xref:System.Windows.FrameworkElement.Width%2A>。</span><span class="sxs-lookup"><span data-stu-id="c9965-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="c9965-110">這種方式，以視覺化方式顯示每個屬性的優先順序。</span><span class="sxs-lookup"><span data-stu-id="c9965-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="c9965-111">下列程式碼後置範例處理事件的<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件引發。</span><span class="sxs-lookup"><span data-stu-id="c9965-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="c9965-112">每個自訂的方法會從輸入<xref:System.Windows.Controls.ListBox>，將做為值剖析<xref:System.Double>，並套用至指定的寬度與相關屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c9965-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="c9965-113">寬度值也會轉換成字串，並寫入至各種<xref:System.Windows.Controls.TextBlock>（定義這些項目未顯示在選取的 XAML） 的項目。</span><span class="sxs-lookup"><span data-stu-id="c9965-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="c9965-114">如需完整範例，請參閱[寬度屬性比較範例](http://go.microsoft.com/fwlink/?LinkID=160050)。</span><span class="sxs-lookup"><span data-stu-id="c9965-114">For the complete sample, see [Width Properties Comparison Sample](http://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9965-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9965-115">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [<span data-ttu-id="c9965-116">面板概觀</span><span class="sxs-lookup"><span data-stu-id="c9965-116">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="c9965-117">設定元素的高度屬性</span><span class="sxs-lookup"><span data-stu-id="c9965-117">Set the Height Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [<span data-ttu-id="c9965-118">寬度屬性比較的範例</span><span class="sxs-lookup"><span data-stu-id="c9965-118">Width Properties Comparison Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160050)
