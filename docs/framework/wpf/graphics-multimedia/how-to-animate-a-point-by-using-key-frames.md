---
title: 操作說明：使用主要畫面格建立點的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344873"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="13b36-102">操作說明：使用主要畫面格建立點的動畫</span><span class="sxs-lookup"><span data-stu-id="13b36-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="13b36-103">此示例演示如何使用 類<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>為 。 <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="13b36-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b36-104">範例</span><span class="sxs-lookup"><span data-stu-id="13b36-104">Example</span></span>  
 <span data-ttu-id="13b36-105">下列範例會沿著三角路徑來移動橢圓形。</span><span class="sxs-lookup"><span data-stu-id="13b36-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="13b36-106">該示例使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>類對 屬性<xref:System.Windows.Media.EllipseGeometry.Center%2A><xref:System.Windows.Media.EllipseGeometry>進行動畫處理。</span><span class="sxs-lookup"><span data-stu-id="13b36-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="13b36-107">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="13b36-107">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="13b36-108">在前半秒，使用<xref:System.Windows.Media.Animation.LinearPointKeyFrame>類的實例以穩定速率從起始位置沿路徑移動橢圓。</span><span class="sxs-lookup"><span data-stu-id="13b36-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="13b36-109">線性關鍵幀（<xref:System.Windows.Media.Animation.LinearPointKeyFrame>如在值之間創建平滑線性插值）。</span><span class="sxs-lookup"><span data-stu-id="13b36-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="13b36-110">在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>類的實例突然沿路徑將橢圓移動到下一個位置。</span><span class="sxs-lookup"><span data-stu-id="13b36-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="13b36-111">離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>如在值之間創建突然跳轉）</span><span class="sxs-lookup"><span data-stu-id="13b36-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3. <span data-ttu-id="13b36-112">在最後兩秒鐘內，使用<xref:System.Windows.Media.Animation.SplinePointKeyFrame>類的實例將橢圓移回其起始位置。</span><span class="sxs-lookup"><span data-stu-id="13b36-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="13b36-113">樣條線鍵幀，<xref:System.Windows.Media.Animation.SplinePointKeyFrame>如根據<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。</span><span class="sxs-lookup"><span data-stu-id="13b36-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="13b36-114">在此範例中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="13b36-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="13b36-115">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="13b36-115">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="13b36-116">為了與其他動畫示例保持一致，此示例的代碼版本使用<xref:System.Windows.Media.Animation.Storyboard>物件來應用 。 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames></span><span class="sxs-lookup"><span data-stu-id="13b36-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="13b36-117">但是，在代碼中應用單個動畫時，使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法而不是 使用 更簡單。 <xref:System.Windows.Media.Animation.Storyboard></span><span class="sxs-lookup"><span data-stu-id="13b36-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="13b36-118">例如，請參閱[在不使用分鏡腳本的情況下為屬性設置動畫](how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="13b36-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b36-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13b36-119">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="13b36-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="13b36-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="13b36-121">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="13b36-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
