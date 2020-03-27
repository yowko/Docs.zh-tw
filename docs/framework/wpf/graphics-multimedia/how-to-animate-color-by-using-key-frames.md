---
title: 操作說明：使用主要畫面格建立色彩的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344741"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="58f3f-102">操作說明：使用主要畫面格建立色彩的動畫</span><span class="sxs-lookup"><span data-stu-id="58f3f-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="58f3f-103">此示例演示如何使用關鍵幀對<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>動畫設置。</span><span class="sxs-lookup"><span data-stu-id="58f3f-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58f3f-104">範例</span><span class="sxs-lookup"><span data-stu-id="58f3f-104">Example</span></span>  
 <span data-ttu-id="58f3f-105">下面的示例使用 類<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.SolidColorBrush>設置<xref:System.Windows.Media.SolidColorBrush.Color%2A>動畫。</span><span class="sxs-lookup"><span data-stu-id="58f3f-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="58f3f-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="58f3f-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="58f3f-107">在前兩秒鐘中<xref:System.Windows.Media.Animation.LinearColorKeyFrame>，使用類的實例逐漸將顏色從綠色更改為紅色。</span><span class="sxs-lookup"><span data-stu-id="58f3f-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="58f3f-108">線性關鍵幀（<xref:System.Windows.Media.Animation.LinearColorKeyFrame>如在值之間創建平滑線性過渡）</span><span class="sxs-lookup"><span data-stu-id="58f3f-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="58f3f-109">在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>類的實例快速將顏色從紅色更改為黃色。</span><span class="sxs-lookup"><span data-stu-id="58f3f-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="58f3f-110">離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>如在值之間創建突然變化）表示，動畫的這一部分中的顏色變化會迅速發生，並且不微妙。</span><span class="sxs-lookup"><span data-stu-id="58f3f-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="58f3f-111">在最後兩秒鐘內<xref:System.Windows.Media.Animation.SplineColorKeyFrame>，使用類的實例再次更改顏色 - 這一次從黃色返回為綠色。</span><span class="sxs-lookup"><span data-stu-id="58f3f-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="58f3f-112">樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineColorKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。</span><span class="sxs-lookup"><span data-stu-id="58f3f-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="58f3f-113">在此範例中，色彩變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="58f3f-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="58f3f-114">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="58f3f-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f3f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58f3f-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="58f3f-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="58f3f-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="58f3f-117">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="58f3f-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
