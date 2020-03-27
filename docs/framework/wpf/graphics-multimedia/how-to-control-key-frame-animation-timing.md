---
title: 如何：控制主要畫面格動畫執行時間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344740"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="ffeb9-102">如何：控制主要畫面格動畫執行時間</span><span class="sxs-lookup"><span data-stu-id="ffeb9-102">How to: Control Key-Frame Animation Timing</span></span>

<span data-ttu-id="ffeb9-103">此示例演示如何控制關鍵幀動畫中關鍵幀的計時。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="ffeb9-104">與其他動畫一樣，關鍵幀動畫具有屬性<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="ffeb9-105">除了指定動畫的持續時間外，還需要指定將該持續時間的哪一部分分配給其每個關鍵幀。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="ffeb9-106">要指定時間，請為動畫中的每個關鍵<xref:System.Windows.Media.Animation.KeyTime>幀指定 a。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>

<span data-ttu-id="ffeb9-107">每個<xref:System.Windows.Media.Animation.KeyTime>關鍵幀指定關鍵幀何時結束（它不指定關鍵幀播放的時間長度）。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="ffeb9-108"><xref:System.Windows.Media.Animation.KeyTime>您可以將 指定<xref:System.TimeSpan>為值、百分比或 或<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>

## <a name="example"></a><span data-ttu-id="ffeb9-109">範例</span><span class="sxs-lookup"><span data-stu-id="ffeb9-109">Example</span></span>

<span data-ttu-id="ffeb9-110">下面的示例使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>在螢幕上為矩形設置動畫。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="ffeb9-111">關鍵幀的鍵時間設置的值<xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

<span data-ttu-id="ffeb9-112">下圖顯示了何時達到每個關鍵幀的值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-112">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ffeb9-113">![在 3、4 和 10 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="ffeb9-113">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>

<span data-ttu-id="ffeb9-114">下一個示例顯示相同的動畫，只不過關鍵幀的鍵時間設置的百分比值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

<span data-ttu-id="ffeb9-115">下圖顯示了何時達到每個關鍵幀的值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-115">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ffeb9-116">![在 3、4 和 10 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="ffeb9-116">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>

<span data-ttu-id="ffeb9-117">下一個示例<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>使用關鍵時間值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

<span data-ttu-id="ffeb9-118">下圖顯示了何時達到每個關鍵幀的值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-118">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ffeb9-119">![在 3.3、6.6 和 9.9 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="ffeb9-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>

<span data-ttu-id="ffeb9-120">最後一個示例<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>使用關鍵時間值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

<span data-ttu-id="ffeb9-121">下圖顯示了何時達到每個關鍵幀的值。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-121">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ffeb9-122">![在 0、5 和 10 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="ffeb9-122">![Key values are reached at 0, 5, and 10 seconds](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>

<span data-ttu-id="ffeb9-123">為簡單起見，此示例的代碼版本使用本地動畫，而不是分鏡腳本，因為只有單個動畫應用於單個屬性，但可以修改示例以改用分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="ffeb9-124">有關如何在代碼中聲明分鏡腳本的示例，請參閱[使用分鏡腳本對屬性進行動畫處理](how-to-animate-a-property-by-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>

<span data-ttu-id="ffeb9-125">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-125">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span> <span data-ttu-id="ffeb9-126">有關關鍵幀動畫的詳細資訊，請參閱[關鍵幀動畫概述](key-frame-animations-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ffeb9-126">For more information about key frame animations, see the [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ffeb9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffeb9-127">See also</span></span>

- [<span data-ttu-id="ffeb9-128">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="ffeb9-128">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="ffeb9-129">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="ffeb9-129">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ffeb9-130">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="ffeb9-130">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
