---
title: 如何：使用主要畫面格建立雙精度浮點數的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 67466bbb5fd7e7a46c312e14666c23048bf43d80
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744663"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="ad209-102">如何：使用主要畫面格建立雙精度浮點數的動畫</span><span class="sxs-lookup"><span data-stu-id="ad209-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="ad209-103">此範例示範如何以動畫顯示採用屬性的值<xref:System.Double>使用主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="ad209-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad209-104">範例</span><span class="sxs-lookup"><span data-stu-id="ad209-104">Example</span></span>  
 <span data-ttu-id="ad209-105">下列範例會讓矩形橫越畫面移動。</span><span class="sxs-lookup"><span data-stu-id="ad209-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="ad209-106">此範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>套用至<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="ad209-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="ad209-107">這個不斷重複的動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="ad209-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="ad209-108">在前三秒內，會使用的執行個體<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>類別將矩形沿著路徑以穩定速率的資料從其起始位置移動到 500 位置。</span><span class="sxs-lookup"><span data-stu-id="ad209-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="ad209-109">線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>建立平滑的線性轉換值之間。</span><span class="sxs-lookup"><span data-stu-id="ad209-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="ad209-110">在第四秒結束時，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>突然將矩形移動到下一個位置的類別。</span><span class="sxs-lookup"><span data-stu-id="ad209-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="ad209-111">特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>建立突然跳躍點之間的值。</span><span class="sxs-lookup"><span data-stu-id="ad209-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="ad209-112">在此範例中，矩形位在起始位置，接著會突然出現在 500 位置。</span><span class="sxs-lookup"><span data-stu-id="ad209-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3.  <span data-ttu-id="ad209-113">在最後兩秒，使用的執行個體<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>類別來將矩形移回起始位置。</span><span class="sxs-lookup"><span data-stu-id="ad209-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="ad209-114">曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ad209-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="ad209-115">在此範例中，矩形一開始會緩慢移動，然後在接近時間區段結尾時以指數方式加速移動。</span><span class="sxs-lookup"><span data-stu-id="ad209-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="ad209-116">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="ad209-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="ad209-117">為了和其他動畫範例保持一致，使用此範例中的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>物件，要套用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。</span><span class="sxs-lookup"><span data-stu-id="ad209-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="ad209-118">或者，套用單一動畫的程式碼中，時，使用的工作變得更容易<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不是使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="ad209-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="ad209-119">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="ad209-119">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad209-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad209-120">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [<span data-ttu-id="ad209-121">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="ad209-121">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="ad209-122">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ad209-122">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
