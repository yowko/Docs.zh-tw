---
title: 操作說明：建立 SolidColorBrush 色彩或不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452879"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="49dc7-102">操作說明：建立 SolidColorBrush 色彩或不透明效果的動畫</span><span class="sxs-lookup"><span data-stu-id="49dc7-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="49dc7-103">這個範例示範如何以動畫顯示 <xref:System.Windows.Media.SolidColorBrush>的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 和 <xref:System.Windows.Media.Brush.Opacity%2A>。</span><span class="sxs-lookup"><span data-stu-id="49dc7-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49dc7-104">範例</span><span class="sxs-lookup"><span data-stu-id="49dc7-104">Example</span></span>  
 <span data-ttu-id="49dc7-105">下列範例會使用三個動畫，以動畫顯示 <xref:System.Windows.Media.SolidColorBrush>的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 和 <xref:System.Windows.Media.Brush.Opacity%2A>。</span><span class="sxs-lookup"><span data-stu-id="49dc7-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
- <span data-ttu-id="49dc7-106">第一個動畫（<xref:System.Windows.Media.Animation.ColorAnimation>）會在滑鼠進入矩形時，將筆刷的色彩變更為 [<xref:System.Windows.Media.Colors.Gray%2A>]。</span><span class="sxs-lookup"><span data-stu-id="49dc7-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
- <span data-ttu-id="49dc7-107">下一個動畫（另一個 <xref:System.Windows.Media.Animation.ColorAnimation>）會在滑鼠離開矩形時，將筆刷的色彩變更為 [<xref:System.Windows.Media.Colors.Orange%2A>]。</span><span class="sxs-lookup"><span data-stu-id="49dc7-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
- <span data-ttu-id="49dc7-108">當按下滑鼠左鍵時，最後一個動畫（<xref:System.Windows.Media.Animation.DoubleAnimation>）會將筆刷的不透明度變更為0.0。</span><span class="sxs-lookup"><span data-stu-id="49dc7-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="49dc7-109">如需更完整的範例，示範如何以動畫顯示不同類型的筆刷，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。</span><span class="sxs-lookup"><span data-stu-id="49dc7-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="49dc7-110">如需動畫的詳細資訊，請參閱[動畫總覽](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="49dc7-110">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="49dc7-111">為了與其他動畫範例保持一致，此範例的程式碼版本會使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來套用其動畫。</span><span class="sxs-lookup"><span data-stu-id="49dc7-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="49dc7-112">不過，在程式碼中套用單一動畫時，使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法比較簡單，而不使用 <xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="49dc7-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="49dc7-113">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="49dc7-113">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49dc7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49dc7-114">See also</span></span>

- [<span data-ttu-id="49dc7-115">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="49dc7-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="49dc7-116">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="49dc7-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="49dc7-117">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="49dc7-117">Brushes Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
