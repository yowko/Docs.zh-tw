---
title: "操作說明：建立 SolidColorBrush 色彩或不透明效果的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 03052cdf68a5a8564d5a24c91521749c10afa6cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="a1aea-102">操作說明：建立 SolidColorBrush 色彩或不透明效果的動畫</span><span class="sxs-lookup"><span data-stu-id="a1aea-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="a1aea-103">此範例示範如何以動畫方式顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>和<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。</span><span class="sxs-lookup"><span data-stu-id="a1aea-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1aea-104">範例</span><span class="sxs-lookup"><span data-stu-id="a1aea-104">Example</span></span>  
 <span data-ttu-id="a1aea-105">下列範例會使用三個動畫以動畫方式顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>和<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。</span><span class="sxs-lookup"><span data-stu-id="a1aea-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
-   <span data-ttu-id="a1aea-106">第一次的動畫， <xref:System.Windows.Media.Animation.ColorAnimation>，筆刷的色彩變更為<xref:System.Windows.Media.Colors.Gray%2A>當滑鼠進入矩形。</span><span class="sxs-lookup"><span data-stu-id="a1aea-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
-   <span data-ttu-id="a1aea-107">下一步的動畫，另一個<xref:System.Windows.Media.Animation.ColorAnimation>，筆刷的色彩變更為<xref:System.Windows.Media.Colors.Orange%2A>當滑鼠離開矩形。</span><span class="sxs-lookup"><span data-stu-id="a1aea-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
-   <span data-ttu-id="a1aea-108">最終的動畫， <xref:System.Windows.Media.Animation.DoubleAnimation>，筆刷的不透明度變更為 0.0，當按下滑鼠左鍵時。</span><span class="sxs-lookup"><span data-stu-id="a1aea-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="a1aea-109">如需更完整的範例，示範如何建立不同類型的筆刷的動畫，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="a1aea-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="a1aea-110">如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a1aea-110">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="a1aea-111">此範例的程式碼版本使用的其他動畫範例的一致性，<xref:System.Windows.Media.Animation.Storyboard>將其動畫套用的物件。</span><span class="sxs-lookup"><span data-stu-id="a1aea-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="a1aea-112">不過，當套用程式碼中的單一動畫，它會更容易使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不要使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="a1aea-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="a1aea-113">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="a1aea-113">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1aea-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1aea-114">See Also</span></span>  
 [<span data-ttu-id="a1aea-115">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a1aea-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a1aea-116">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="a1aea-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="a1aea-117">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="a1aea-117">Brushes Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159973)
