---
title: "操作說明：使用主要畫面格建立框線粗細的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f255ff38ec7ee79f02a0cd40a3f0143c36e1c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="29554-102">操作說明：使用主要畫面格建立框線粗細的動畫</span><span class="sxs-lookup"><span data-stu-id="29554-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="29554-103">此範例示範如何以動畫方式顯示<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="29554-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29554-104">範例</span><span class="sxs-lookup"><span data-stu-id="29554-104">Example</span></span>  
 <span data-ttu-id="29554-105">下列範例會使用<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="29554-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="29554-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="29554-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="29554-107">在第一個半秒，會使用的執行個體<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>類別來逐漸增加框線的粗細。</span><span class="sxs-lookup"><span data-stu-id="29554-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="29554-108">此範例會使用<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>建立平滑的線性增加值之間。</span><span class="sxs-lookup"><span data-stu-id="29554-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="29554-109">在下一個結尾半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>類別以突然增加框線的粗細。</span><span class="sxs-lookup"><span data-stu-id="29554-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="29554-110">特定的主要畫面格，例如衍生自<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>建立突然跳躍點之間的值，也就是為動畫移動不穩定。</span><span class="sxs-lookup"><span data-stu-id="29554-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="29554-111">在最後的兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>類別，以減少框線的粗細。</span><span class="sxs-lookup"><span data-stu-id="29554-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="29554-112">曲線主要畫面格一樣衍生自<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="29554-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="29554-113">在此主要畫面格中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="29554-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="29554-114">如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="29554-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29554-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="29554-115">See Also</span></span>  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [<span data-ttu-id="29554-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="29554-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="29554-117">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="29554-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [<span data-ttu-id="29554-118">建立 BorderThickness 值的動畫</span><span class="sxs-lookup"><span data-stu-id="29554-118">Animate a BorderThickness Value</span></span>](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
