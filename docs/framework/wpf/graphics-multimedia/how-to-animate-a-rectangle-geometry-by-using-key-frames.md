---
title: 操作說明：使用主要畫面格建立矩形幾何的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344684"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="3b686-102">操作說明：使用主要畫面格建立矩形幾何的動畫</span><span class="sxs-lookup"><span data-stu-id="3b686-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="3b686-103">此示例演示如何使用關鍵幀對<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>進行動畫處理。</span><span class="sxs-lookup"><span data-stu-id="3b686-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b686-104">範例</span><span class="sxs-lookup"><span data-stu-id="3b686-104">Example</span></span>  
 <span data-ttu-id="3b686-105">下面的示例使用 類<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.RectangleGeometry>設置<xref:System.Windows.Media.RectangleGeometry.Rect%2A>動畫。</span><span class="sxs-lookup"><span data-stu-id="3b686-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="3b686-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="3b686-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="3b686-107">在前兩秒鐘內<xref:System.Windows.Media.Animation.LinearRectKeyFrame>，使用類的實例對矩形的位置、寬度和高度進行動畫處理。</span><span class="sxs-lookup"><span data-stu-id="3b686-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="3b686-108">線性關鍵幀（<xref:System.Windows.Media.Animation.LinearRectKeyFrame>如在值之間創建平滑線性過渡）</span><span class="sxs-lookup"><span data-stu-id="3b686-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="3b686-109">在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>類的實例突然降低矩形的高度。</span><span class="sxs-lookup"><span data-stu-id="3b686-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="3b686-110">離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>如在值之間創建突然變化）表示，高度的降低會迅速發生，並且不微妙。</span><span class="sxs-lookup"><span data-stu-id="3b686-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="3b686-111">在最後兩秒鐘內<xref:System.Windows.Media.Animation.SplineRectKeyFrame>，使用類的實例將矩形更改回其原始大小和位置。</span><span class="sxs-lookup"><span data-stu-id="3b686-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="3b686-112">樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineRectKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。</span><span class="sxs-lookup"><span data-stu-id="3b686-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="3b686-113">在此範例中，變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="3b686-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="3b686-114">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="3b686-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b686-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b686-115">See also</span></span>

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="3b686-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="3b686-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="3b686-117">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="3b686-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
