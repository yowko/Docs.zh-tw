---
title: HOW TO：使用主要畫面格建立鏡頭位置和方向的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 5df3a201eaae4ddcf2e5d5aac3de6e0d5013947c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353396"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="df0a0-102">HOW TO：使用主要畫面格建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="df0a0-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="df0a0-103">在下列範例中，<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>用來以動畫顯示的位置<xref:System.Windows.Media.Media3D.PerspectiveCamera>3D 場景中。</span><span class="sxs-lookup"><span data-stu-id="df0a0-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="df0a0-104">颾魤 ㄛ<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>用來以動畫顯示 3D 場景中指向觀景窗的方向。</span><span class="sxs-lookup"><span data-stu-id="df0a0-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="df0a0-105">這兩個動畫使用數個主要畫面格建立一系列的動畫效果：</span><span class="sxs-lookup"><span data-stu-id="df0a0-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1.  <span data-ttu-id="df0a0-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> 和<xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>用來建立值之間的平滑的線性插補。</span><span class="sxs-lookup"><span data-stu-id="df0a0-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="df0a0-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> 和<xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>用來建立突然 「 跳躍點 」 值 （沒有插補） 之間。</span><span class="sxs-lookup"><span data-stu-id="df0a0-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="df0a0-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> 並<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>用來建立變數轉換取決於值之間<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="df0a0-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="df0a0-109">下列範例中，在動畫啟動很緩慢，但接近時間區段結尾時，以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="df0a0-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df0a0-110">範例</span><span class="sxs-lookup"><span data-stu-id="df0a0-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="df0a0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df0a0-111">See also</span></span>
- [<span data-ttu-id="df0a0-112">在立體場景中建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="df0a0-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="df0a0-113">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="df0a0-113">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
