---
title: 如何：使用主要畫面格建立布林值的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: d6273c08881e802595e831cafe120a5bec841c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556922"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="a61c2-102">如何：使用主要畫面格建立布林值的動畫</span><span class="sxs-lookup"><span data-stu-id="a61c2-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="a61c2-103">這個範例示範如何建立動畫的布林屬性值<xref:System.Windows.Controls.Button>控制項使用的主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="a61c2-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a61c2-104">範例</span><span class="sxs-lookup"><span data-stu-id="a61c2-104">Example</span></span>  
 <span data-ttu-id="a61c2-105">下列範例會使用<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.UIElement.IsEnabled%2A>屬性<xref:System.Windows.Controls.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="a61c2-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="a61c2-106">在此範例中的所有主要畫面格使用的執行個體<xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>類別。</span><span class="sxs-lookup"><span data-stu-id="a61c2-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="a61c2-107">獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>建立突然跳躍點之間的值，也就是為動畫移動不穩定。</span><span class="sxs-lookup"><span data-stu-id="a61c2-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a61c2-108">如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="a61c2-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61c2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a61c2-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="a61c2-110">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a61c2-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a61c2-111">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="a61c2-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
