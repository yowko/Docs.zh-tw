---
title: "如何：將 UIElement 設為透明或半透明"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25245319c02ae376410d71afb7a1e56eda259e99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="83363-102">如何：將 UIElement 設為透明或半透明</span><span class="sxs-lookup"><span data-stu-id="83363-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="83363-103">這個範例示範如何讓<xref:System.Windows.UIElement>透明或半透明。</span><span class="sxs-lookup"><span data-stu-id="83363-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="83363-104">請讓元素透明或半透明效果，您將設定其<xref:System.Windows.UIElement.Opacity%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="83363-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="83363-105">值為`0.0`完全透明，而值為類型建立項目`1.0`完全不透明類型建立項目。</span><span class="sxs-lookup"><span data-stu-id="83363-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="83363-106">值為`0.5`類型建立項目 50%不透明，依此類推。</span><span class="sxs-lookup"><span data-stu-id="83363-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="83363-107">項目的<xref:System.Windows.UIElement.Opacity%2A>設`1.0`預設。</span><span class="sxs-lookup"><span data-stu-id="83363-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83363-108">範例</span><span class="sxs-lookup"><span data-stu-id="83363-108">Example</span></span>  
 <span data-ttu-id="83363-109">下列範例會設定<xref:System.Windows.UIElement.Opacity%2A>的按鈕`0.25`，讓它和其內容 （在此情況下，按鈕的文字） 25%不透明。</span><span class="sxs-lookup"><span data-stu-id="83363-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="83363-110">如果項目的內容有其自己<xref:System.Windows.UIElement.Opacity%2A>設定，這些值會乘以內含項目<xref:System.Windows.UIElement.Opacity%2A>。</span><span class="sxs-lookup"><span data-stu-id="83363-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="83363-111">下列範例會設定按鈕的<xref:System.Windows.UIElement.Opacity%2A>至`0.25`，而<xref:System.Windows.UIElement.Opacity%2A>的<xref:System.Windows.Controls.Image>控制項中的按鈕，以包含與`0.5`。</span><span class="sxs-lookup"><span data-stu-id="83363-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="83363-112">如此一來，此影像隨即顯示 12.5%不透明： 0.25 * 0.5 = 0.125。</span><span class="sxs-lookup"><span data-stu-id="83363-112">As a result, the image appears 12.5% opaque: 0.25 * 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="83363-113">若要控制的項目不透明度的另一個方法是設定的不透明度<xref:System.Windows.Media.Brush>繪製項目。</span><span class="sxs-lookup"><span data-stu-id="83363-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="83363-114">這種方法可讓您選擇性地變更的部分項目的不透明度，並提供效能優勢，透過使用項目的<xref:System.Windows.UIElement.Opacity%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="83363-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="83363-115">下列範例會設定<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>用來繪製按鈕的<xref:System.Windows.Controls.Control.Background%2A>設`0.25`。</span><span class="sxs-lookup"><span data-stu-id="83363-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="83363-116">如此一來，背景的筆刷為 25%不透明，但其內容 （按鈕的文字） 保持 100%不透明。</span><span class="sxs-lookup"><span data-stu-id="83363-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="83363-117">您也可以控制筆刷內的個別色彩的不的透明度。</span><span class="sxs-lookup"><span data-stu-id="83363-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="83363-118">如需有關色彩和筆刷的詳細資訊，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="83363-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="83363-119">如需顯示如何建立動畫項目的不透明度的範例，請參閱[以動畫顯示的項目或筆刷的不透明度](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)。</span><span class="sxs-lookup"><span data-stu-id="83363-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
