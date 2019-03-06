---
title: HOW TO：使用主要畫面格建立點的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: 4eeb7aa271883e1c76d5cac77f49accbdff39aea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357231"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="48d03-102">HOW TO：使用主要畫面格建立點的動畫</span><span class="sxs-lookup"><span data-stu-id="48d03-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="48d03-103">此範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Point>。</span><span class="sxs-lookup"><span data-stu-id="48d03-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48d03-104">範例</span><span class="sxs-lookup"><span data-stu-id="48d03-104">Example</span></span>  
 <span data-ttu-id="48d03-105">下列範例會沿著三角路徑來移動橢圓形。</span><span class="sxs-lookup"><span data-stu-id="48d03-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="48d03-106">此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性<xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="48d03-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="48d03-107">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="48d03-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="48d03-108">在前半秒，期間使用的執行個體<xref:System.Windows.Media.Animation.LinearPointKeyFrame>將橢圓形沿著路徑以穩定速率，從其起始位置的類別。</span><span class="sxs-lookup"><span data-stu-id="48d03-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="48d03-109">線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearPointKeyFrame>建立平滑的線性插補值之間。</span><span class="sxs-lookup"><span data-stu-id="48d03-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="48d03-110">下一步 結束期間半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>突然將橢圓形沿著路徑移動到下一個位置的類別。</span><span class="sxs-lookup"><span data-stu-id="48d03-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="48d03-111">特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>建立突然跳躍點之間的值。</span><span class="sxs-lookup"><span data-stu-id="48d03-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="48d03-112">在最後的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.SplinePointKeyFrame>類別來將橢圓形移回起始位置。</span><span class="sxs-lookup"><span data-stu-id="48d03-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="48d03-113">曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplinePointKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="48d03-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="48d03-114">在此範例中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="48d03-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="48d03-115">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="48d03-115">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="48d03-116">為了和其他動畫範例保持一致，使用此範例中的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>物件，要套用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>。</span><span class="sxs-lookup"><span data-stu-id="48d03-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="48d03-117">不過，套用單一動畫的程式碼中，時，使用的工作變得更容易<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不是使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="48d03-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="48d03-118">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="48d03-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d03-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48d03-119">See also</span></span>
- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="48d03-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="48d03-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="48d03-121">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="48d03-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
