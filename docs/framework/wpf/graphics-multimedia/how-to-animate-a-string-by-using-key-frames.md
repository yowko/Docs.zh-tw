---
title: 使用主要畫面格建立字串的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344676"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="15c4d-102">使用主要畫面格建立字串的動畫</span><span class="sxs-lookup"><span data-stu-id="15c4d-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="15c4d-103">此示例演示如何使用關鍵幀為字串設置動畫，在此示例中，該字串是<xref:System.Windows.Controls.ContentControl.Content%2A><xref:System.Windows.Controls.Button>控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="15c4d-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15c4d-104">範例</span><span class="sxs-lookup"><span data-stu-id="15c4d-104">Example</span></span>  
 <span data-ttu-id="15c4d-105">下面的示例使用 類<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Controls.Button>設置<xref:System.Windows.Controls.ContentControl.Content%2A>動畫。</span><span class="sxs-lookup"><span data-stu-id="15c4d-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="15c4d-106">此示例中的所有關鍵幀都使用類的實例，<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>因為使用關鍵幀創建的字串動畫只能使用離散關鍵幀。</span><span class="sxs-lookup"><span data-stu-id="15c4d-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="15c4d-107">離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>如在值之間創建突然跳轉），即動畫更改發生得很快，並且不是微妙的。</span><span class="sxs-lookup"><span data-stu-id="15c4d-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="15c4d-108">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="15c4d-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c4d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15c4d-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="15c4d-110">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="15c4d-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="15c4d-111">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="15c4d-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
