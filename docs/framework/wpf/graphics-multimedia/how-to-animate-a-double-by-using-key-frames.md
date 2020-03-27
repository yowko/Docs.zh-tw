---
title: 操作說明：使用主要畫面格建立雙精度浮點數的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344947"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="f8485-102">操作說明：使用主要畫面格建立雙精度浮點數的動畫</span><span class="sxs-lookup"><span data-stu-id="f8485-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="f8485-103">此示例演示如何使用關鍵幀對 獲取 的屬性<xref:System.Double>的值設置動畫。</span><span class="sxs-lookup"><span data-stu-id="f8485-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8485-104">範例</span><span class="sxs-lookup"><span data-stu-id="f8485-104">Example</span></span>  
 <span data-ttu-id="f8485-105">下列範例會讓矩形橫越畫面移動。</span><span class="sxs-lookup"><span data-stu-id="f8485-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="f8485-106">該示例使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>類為應用於<xref:System.Windows.Media.TranslateTransform.X%2A>的屬性<xref:System.Windows.Media.TranslateTransform>設置動畫<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="f8485-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="f8485-107">這個不斷重複的動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="f8485-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="f8485-108">在前三秒內，使用<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>類的實例以穩定速率沿路徑移動矩形，從起始位置移動到 500 位置。</span><span class="sxs-lookup"><span data-stu-id="f8485-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="f8485-109">線性關鍵幀（<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>如在值之間創建平滑線性過渡）</span><span class="sxs-lookup"><span data-stu-id="f8485-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="f8485-110">在第四秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>類的實例突然將矩形移動到下一個位置。</span><span class="sxs-lookup"><span data-stu-id="f8485-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="f8485-111">離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>如在值之間創建突然跳轉）</span><span class="sxs-lookup"><span data-stu-id="f8485-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="f8485-112">在此範例中，矩形位在起始位置，接著會突然出現在 500 位置。</span><span class="sxs-lookup"><span data-stu-id="f8485-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3. <span data-ttu-id="f8485-113">在最後兩秒鐘中，使用類的<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>實例將矩形移回其起始位置。</span><span class="sxs-lookup"><span data-stu-id="f8485-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="f8485-114">樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。</span><span class="sxs-lookup"><span data-stu-id="f8485-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="f8485-115">在此範例中，矩形一開始會緩慢移動，然後在接近時間區段結尾時以指數方式加速移動。</span><span class="sxs-lookup"><span data-stu-id="f8485-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f8485-116">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="f8485-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="f8485-117">為了與其他動畫示例保持一致，此示例的代碼版本使用<xref:System.Windows.Media.Animation.Storyboard>物件來應用 。 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames></span><span class="sxs-lookup"><span data-stu-id="f8485-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="f8485-118">或者，在代碼中應用單個動畫時，使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法而不是 使用 更簡單。 <xref:System.Windows.Media.Animation.Storyboard></span><span class="sxs-lookup"><span data-stu-id="f8485-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="f8485-119">例如，請參閱[在不使用分鏡腳本的情況下為屬性設置動畫](how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="f8485-119">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8485-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8485-120">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [<span data-ttu-id="f8485-121">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="f8485-121">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="f8485-122">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="f8485-122">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
