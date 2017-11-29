---
title: "操作說明：使用主要畫面格建立大小變更的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9577f9f08fa1d19aa214bda5a1aef997c2cfa2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="c6432-102">操作說明：使用主要畫面格建立大小變更的動畫</span><span class="sxs-lookup"><span data-stu-id="c6432-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="c6432-103">這個範例示範如何使用主要畫面格建立大小變更的動畫。</span><span class="sxs-lookup"><span data-stu-id="c6432-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6432-104">範例</span><span class="sxs-lookup"><span data-stu-id="c6432-104">Example</span></span>  
 <span data-ttu-id="c6432-105">下列範例會使用<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.ArcSegment.Size%2A>屬性<xref:System.Windows.Media.ArcSegment>。</span><span class="sxs-lookup"><span data-stu-id="c6432-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="c6432-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="c6432-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="c6432-107">在第一個半秒數的動畫，會使用的執行個體<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>類別來逐漸增加弧線的大小。線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>建立值之間的平順地線性轉換。</span><span class="sxs-lookup"><span data-stu-id="c6432-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="c6432-108">在下一個結尾半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>類別突然增加弧線的大小。獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>建立突然跳躍點之間的值，也就是，大小變更突然出現，並不會出現細微。</span><span class="sxs-lookup"><span data-stu-id="c6432-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="c6432-109">在最後的兩秒，使用 執行個體<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>弧線的大小增加的類別。曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c6432-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="c6432-110">在此範例中，弧線的大小一開始會緩慢增加，然後在接近時間區段結尾時以指數方式增加。</span><span class="sxs-lookup"><span data-stu-id="c6432-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="c6432-111">如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="c6432-111">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6432-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6432-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [<span data-ttu-id="c6432-113">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="c6432-113">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="c6432-114">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="c6432-114">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
