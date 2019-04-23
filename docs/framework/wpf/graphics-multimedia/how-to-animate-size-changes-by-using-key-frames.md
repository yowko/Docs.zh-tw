---
title: HOW TO：使用主要畫面格建立大小變更的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0629b6600444bd172af451fd7e970bff894d8047
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342358"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="d8342-102">HOW TO：使用主要畫面格建立大小變更的動畫</span><span class="sxs-lookup"><span data-stu-id="d8342-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="d8342-103">這個範例示範如何使用主要畫面格建立大小變更的動畫。</span><span class="sxs-lookup"><span data-stu-id="d8342-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8342-104">範例</span><span class="sxs-lookup"><span data-stu-id="d8342-104">Example</span></span>  
 <span data-ttu-id="d8342-105">下列範例會使用<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.ArcSegment.Size%2A>屬性<xref:System.Windows.Media.ArcSegment>。</span><span class="sxs-lookup"><span data-stu-id="d8342-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="d8342-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="d8342-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="d8342-107">在動畫的前半秒，期間使用的執行個體<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>類別來逐漸增加弧線的大小。線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>建立平滑的線性轉換值之間。</span><span class="sxs-lookup"><span data-stu-id="d8342-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="d8342-108">在下一步結尾半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>類別來突然增加弧線的大小。特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>建立突然跳躍點之間的值，也就是，突然發生大小變更，而不是微量。</span><span class="sxs-lookup"><span data-stu-id="d8342-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="d8342-109">最後兩秒，透過使用的執行個體<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>類別來增加弧線的大小。曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d8342-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="d8342-110">在此範例中，弧線的大小一開始會緩慢增加，然後在接近時間區段結尾時以指數方式增加。</span><span class="sxs-lookup"><span data-stu-id="d8342-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="d8342-111">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="d8342-111">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8342-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8342-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="d8342-113">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="d8342-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="d8342-114">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="d8342-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
