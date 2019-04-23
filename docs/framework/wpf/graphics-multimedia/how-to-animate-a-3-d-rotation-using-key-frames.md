---
title: HOW TO：3d 旋轉的動畫使用主要畫面格
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: e72ec94f830f0f5001a77e7492aa1326a47b309d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297989"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="9fade-102">HOW TO：3d 旋轉的動畫使用主要畫面格</span><span class="sxs-lookup"><span data-stu-id="9fade-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="9fade-103">在下列範例中，<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>用來製作 3D 物件旋轉時其旋轉軸以動畫顯示導致"搖晃"。</span><span class="sxs-lookup"><span data-stu-id="9fade-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="9fade-104">這個動畫會使用下列的主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="9fade-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="9fade-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> 用來建立值之間的平滑的線性插補。</span><span class="sxs-lookup"><span data-stu-id="9fade-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="9fade-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> 用來建立突然 「 跳躍點 」 值 （沒有插補） 之間。</span><span class="sxs-lookup"><span data-stu-id="9fade-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="9fade-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> 用來建立變數轉換取決於值之間<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9fade-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="9fade-108">在下列範例中，動畫的這個部分很緩慢，但接近時間區段結尾開始，以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="9fade-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fade-109">範例</span><span class="sxs-lookup"><span data-stu-id="9fade-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9fade-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fade-110">See also</span></span>

- [<span data-ttu-id="9fade-111">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="9fade-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="9fade-112">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="9fade-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="9fade-113">使用分鏡腳本建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="9fade-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="9fade-114">使用 Rotation3DAnimation 建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="9fade-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="9fade-115">使用四元數建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="9fade-115">Animate a 3-D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="9fade-116">使用主要畫面格建立立體旋轉的動畫 (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="9fade-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
