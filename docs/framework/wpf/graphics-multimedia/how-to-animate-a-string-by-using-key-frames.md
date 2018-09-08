---
title: 使用主要畫面格建立字串的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 1b55afd5938073a326789e67b66fec9cfce12015
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189247"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="f60b3-102">使用主要畫面格建立字串的動畫</span><span class="sxs-lookup"><span data-stu-id="f60b3-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="f60b3-103">此範例示範如何以動畫顯示的字串，在此範例中是<xref:System.Windows.Controls.ContentControl.Content%2A>屬性<xref:System.Windows.Controls.Button>控制項，使用主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="f60b3-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f60b3-104">範例</span><span class="sxs-lookup"><span data-stu-id="f60b3-104">Example</span></span>  
 <span data-ttu-id="f60b3-105">下列範例會使用<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Controls.ContentControl.Content%2A>屬性<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="f60b3-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="f60b3-106">在此範例中的所有主要畫面格使用的執行個體<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>類別，因為會使用主要畫面格建立字串動畫只能使用特定主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="f60b3-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="f60b3-107">特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>建立突然跳躍點之間的值，也就是，動畫的變更會快速發生，而不是微量。</span><span class="sxs-lookup"><span data-stu-id="f60b3-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f60b3-108">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="f60b3-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60b3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f60b3-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [<span data-ttu-id="f60b3-110">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="f60b3-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="f60b3-111">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="f60b3-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
