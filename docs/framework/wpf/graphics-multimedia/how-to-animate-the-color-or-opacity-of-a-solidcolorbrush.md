---
title: HOW TO：建立 SolidColorBrush 色彩或不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: a6bd7f27f1cce6169181640bb52edad4a493c228
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738689"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="adb70-102">HOW TO：建立 SolidColorBrush 色彩或不透明效果的動畫</span><span class="sxs-lookup"><span data-stu-id="adb70-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="adb70-103">此範例示範如何建立動畫<xref:System.Windows.Media.SolidColorBrush.Color%2A>並<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。</span><span class="sxs-lookup"><span data-stu-id="adb70-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb70-104">範例</span><span class="sxs-lookup"><span data-stu-id="adb70-104">Example</span></span>  
 <span data-ttu-id="adb70-105">下列範例會使用三個動畫以動畫顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>並<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。</span><span class="sxs-lookup"><span data-stu-id="adb70-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
-   <span data-ttu-id="adb70-106">第一次的動畫<xref:System.Windows.Media.Animation.ColorAnimation>，將筆刷的色彩變更為<xref:System.Windows.Media.Colors.Gray%2A>當滑鼠進入矩形。</span><span class="sxs-lookup"><span data-stu-id="adb70-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
-   <span data-ttu-id="adb70-107">下一個動畫為另一個<xref:System.Windows.Media.Animation.ColorAnimation>，將筆刷的色彩變更為<xref:System.Windows.Media.Colors.Orange%2A>當滑鼠離開矩形。</span><span class="sxs-lookup"><span data-stu-id="adb70-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
-   <span data-ttu-id="adb70-108">最終的動畫， <xref:System.Windows.Media.Animation.DoubleAnimation>，筆刷的不透明度變更為 0.0，當按下滑鼠左鍵時。</span><span class="sxs-lookup"><span data-stu-id="adb70-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="adb70-109">如需更完整的範例，示範如何以動畫顯示不同類型的筆刷，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="adb70-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="adb70-110">如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="adb70-110">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="adb70-111">為了和其他動畫範例保持一致，此範例中的程式碼版本使用<xref:System.Windows.Media.Animation.Storyboard>來套用其動畫的物件。</span><span class="sxs-lookup"><span data-stu-id="adb70-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="adb70-112">不過，套用單一動畫的程式碼中，時，使用的工作變得更容易<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不是使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="adb70-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="adb70-113">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="adb70-113">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb70-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adb70-114">See also</span></span>
- [<span data-ttu-id="adb70-115">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="adb70-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="adb70-116">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="adb70-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
- [<span data-ttu-id="adb70-117">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="adb70-117">Brushes Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159973)
