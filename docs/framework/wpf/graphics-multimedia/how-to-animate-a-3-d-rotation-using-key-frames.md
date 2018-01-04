---
title: "如何：使用主要畫面格建立立體旋轉的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca1b49277792e89f1d0cc7ca213d02978bb4dee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="ec903-102">如何：使用主要畫面格建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="ec903-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="ec903-103">在下列範例中，<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>用來進行時其軸的旋轉動畫導致"微微"旋轉的 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="ec903-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="ec903-104">這個動畫會使用下列的主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="ec903-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="ec903-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>用來建立值之間的順暢、 線性插補。</span><span class="sxs-lookup"><span data-stu-id="ec903-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="ec903-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>用來建立突然"跳躍點 」 值 （沒有插補） 之間。</span><span class="sxs-lookup"><span data-stu-id="ec903-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="ec903-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>用來建立變數取決於值之間轉換<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ec903-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="ec903-108">在下列範例中，動畫這部分很緩慢但時間區段的結尾開始，加速以等比級數。</span><span class="sxs-lookup"><span data-stu-id="ec903-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec903-109">範例</span><span class="sxs-lookup"><span data-stu-id="ec903-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ec903-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec903-110">See Also</span></span>  
 [<span data-ttu-id="ec903-111">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="ec903-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="ec903-112">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="ec903-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="ec903-113">使用分鏡腳本建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="ec903-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="ec903-114">使用 Rotation3DAnimation 建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="ec903-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="ec903-115">使用四元數建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="ec903-115">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="ec903-116">使用主要畫面格建立立體旋轉的動畫 (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="ec903-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
