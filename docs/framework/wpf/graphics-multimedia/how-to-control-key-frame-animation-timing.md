---
title: 如何：控制主要畫面格動畫執行時間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: d65bf6f7643adf1d98d468853ae8017a4a6554ac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401234"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="a934d-102">如何：控制主要畫面格動畫執行時間</span><span class="sxs-lookup"><span data-stu-id="a934d-102">How to: Control Key-Frame Animation Timing</span></span>
<span data-ttu-id="a934d-103">此範例示範如何控制主要畫面格動畫中的主要畫面格的時間。</span><span class="sxs-lookup"><span data-stu-id="a934d-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="a934d-104">如同其他動畫，主要畫面格動畫也有<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a934d-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="a934d-105">除了指定動畫的持續時間，您必須指定這段期間的哪個部分配置給每個主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="a934d-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="a934d-106">若要配置的時間，您指定<xref:System.Windows.Media.Animation.KeyTime>動畫中的每個主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="a934d-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>  
  
 <span data-ttu-id="a934d-107"><xref:System.Windows.Media.Animation.KeyTime>時的主要畫面格結束 （它未指定主要畫面格播放的時間長度），指定每個主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="a934d-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="a934d-108">您可以指定<xref:System.Windows.Media.Animation.KeyTime>作為<xref:System.TimeSpan>值，以百分比表示，或作為<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>或<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊值。</span><span class="sxs-lookup"><span data-stu-id="a934d-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a934d-109">範例</span><span class="sxs-lookup"><span data-stu-id="a934d-109">Example</span></span>  
 <span data-ttu-id="a934d-110">下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>來建立矩形動畫在螢幕上。</span><span class="sxs-lookup"><span data-stu-id="a934d-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="a934d-111">主要畫面格的關鍵時間會以設定<xref:System.TimeSpan>值。</span><span class="sxs-lookup"><span data-stu-id="a934d-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 <span data-ttu-id="a934d-112">下圖顯示當達到每個主要畫面格的值。</span><span class="sxs-lookup"><span data-stu-id="a934d-112">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="a934d-113">![索引鍵值 3、 4 和 10 秒時到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="a934d-113">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>  
  
 <span data-ttu-id="a934d-114">下一個範例顯示的完全相同，不同之處在於主要畫面格的關鍵時間會以百分比值來設定的動畫。</span><span class="sxs-lookup"><span data-stu-id="a934d-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 <span data-ttu-id="a934d-115">下圖顯示當達到每個主要畫面格的值。</span><span class="sxs-lookup"><span data-stu-id="a934d-115">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="a934d-116">![索引鍵值 3、 4 和 10 秒時到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="a934d-116">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>  
  
 <span data-ttu-id="a934d-117">下一個範例使用<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>索引鍵時間值。</span><span class="sxs-lookup"><span data-stu-id="a934d-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 <span data-ttu-id="a934d-118">下圖顯示當達到每個主要畫面格的值。</span><span class="sxs-lookup"><span data-stu-id="a934d-118">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="a934d-119">![在 3.3、 6.6 和 9.9 秒時到達索引鍵值](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="a934d-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>  
  
 <span data-ttu-id="a934d-120">最後一個範例會使用<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>索引鍵時間值。</span><span class="sxs-lookup"><span data-stu-id="a934d-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 <span data-ttu-id="a934d-121">下圖顯示當達到每個主要畫面格的值。</span><span class="sxs-lookup"><span data-stu-id="a934d-121">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="a934d-122">![在 0、 5 和 10 秒的索引鍵的值時到達各個](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="a934d-122">![Key values are reached at 0, 5, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>  
  
 <span data-ttu-id="a934d-123">為了簡單起見，此範例使用本機動畫的程式碼版本不分鏡腳本，因為只有單一動畫套用至單一屬性，但範例可以修改成改為使用分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a934d-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="a934d-124">如需示範如何宣告在程式碼中的分鏡腳本的範例，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="a934d-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="a934d-125">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="a934d-125">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span> <span data-ttu-id="a934d-126">如需有關主要畫面格動畫的詳細資訊，請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a934d-126">For more information about key frame animations, see the [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a934d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a934d-127">See Also</span></span>  
 [<span data-ttu-id="a934d-128">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a934d-128">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a934d-129">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a934d-129">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a934d-130">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="a934d-130">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
