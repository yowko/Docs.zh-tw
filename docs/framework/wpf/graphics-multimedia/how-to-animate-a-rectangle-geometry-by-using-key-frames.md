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
ms.openlocfilehash: 9b4a620ea58026c3be1b09d01a595e965e4c2b45
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518776"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="2950b-102">操作說明：使用主要畫面格建立矩形幾何的動畫</span><span class="sxs-lookup"><span data-stu-id="2950b-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="2950b-103">此範例示範如何建立動畫<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>使用主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="2950b-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2950b-104">範例</span><span class="sxs-lookup"><span data-stu-id="2950b-104">Example</span></span>  
 <span data-ttu-id="2950b-105">下列範例會使用<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>。</span><span class="sxs-lookup"><span data-stu-id="2950b-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="2950b-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="2950b-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="2950b-107">在前的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.LinearRectKeyFrame>類別以動畫顯示的位置、 寬度和高度的矩形逐漸變更。</span><span class="sxs-lookup"><span data-stu-id="2950b-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="2950b-108">線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearRectKeyFrame>建立平滑的線性轉換值之間。</span><span class="sxs-lookup"><span data-stu-id="2950b-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="2950b-109">下一步 結束期間半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>突然減少矩形的高度的類別。</span><span class="sxs-lookup"><span data-stu-id="2950b-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="2950b-110">特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>突然之間建立變更的值，也就是，高度降低很快就會完成，而不是微量。</span><span class="sxs-lookup"><span data-stu-id="2950b-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="2950b-111">在最後的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.SplineRectKeyFrame>類別，以變更回其原始大小和位置的矩形。</span><span class="sxs-lookup"><span data-stu-id="2950b-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="2950b-112">曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineRectKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2950b-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="2950b-113">在此範例中，變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="2950b-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="2950b-114">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="2950b-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2950b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2950b-115">See Also</span></span>  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [<span data-ttu-id="2950b-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="2950b-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="2950b-117">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="2950b-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
