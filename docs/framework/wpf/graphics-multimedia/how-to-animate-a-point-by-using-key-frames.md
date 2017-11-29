---
title: "操作說明：使用主要畫面格建立點的動畫"
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
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f574f85a5840e8bbe2d6c026d57a4cc28bd8a797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="3cbb9-102">操作說明：使用主要畫面格建立點的動畫</span><span class="sxs-lookup"><span data-stu-id="3cbb9-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="3cbb9-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Point>。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cbb9-104">範例</span><span class="sxs-lookup"><span data-stu-id="3cbb9-104">Example</span></span>  
 <span data-ttu-id="3cbb9-105">下列範例會沿著三角路徑來移動橢圓形。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="3cbb9-106">此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性<xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="3cbb9-107">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="3cbb9-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="3cbb9-108">在第一個半秒，會使用的執行個體<xref:System.Windows.Media.Animation.LinearPointKeyFrame>沿著路徑橢圓形移交穩定的速率，從其起始位置的類別。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="3cbb9-109">線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearPointKeyFrame>建立平滑的線性插補值之間。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="3cbb9-110">在下個結束半秒，會使用的執行個體<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>突然移動路徑上的橢圓形的下一個位置的類別。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="3cbb9-111">獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>建立值之間的突然跳躍點。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="3cbb9-112">在最後的兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.SplinePointKeyFrame>類別，以將橢圓形移回其開始位置。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="3cbb9-113">曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplinePointKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="3cbb9-114">在此範例中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="3cbb9-115">如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-115">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="3cbb9-116">此範例的程式碼版本使用的其他動畫範例的一致性，<xref:System.Windows.Media.Animation.Storyboard>物件以套用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="3cbb9-117">不過，當套用程式碼中的單一動畫，它會更容易使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不要使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="3cbb9-118">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="3cbb9-118">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbb9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cbb9-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [<span data-ttu-id="3cbb9-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="3cbb9-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="3cbb9-121">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="3cbb9-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
