---
title: "如何：使用主要畫面格建立鏡頭位置和方向的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbac99770b5cbb7dacb0468e1a892956fda6b79c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="147e5-102">如何：使用主要畫面格建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="147e5-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="147e5-103">在下列範例中，<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>用來建立動畫的位置<xref:System.Windows.Media.Media3D.PerspectiveCamera>3D 場景中。</span><span class="sxs-lookup"><span data-stu-id="147e5-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="147e5-104">此外，<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>會相機指向的 3D 場景方向的動畫。</span><span class="sxs-lookup"><span data-stu-id="147e5-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="147e5-105">這兩個動畫使用數個主要畫面格來建立一系列的動畫效果：</span><span class="sxs-lookup"><span data-stu-id="147e5-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1.  <span data-ttu-id="147e5-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>和<xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>用來建立值之間的順暢、 線性插補。</span><span class="sxs-lookup"><span data-stu-id="147e5-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="147e5-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>和<xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>用來建立突然"跳躍點 」 值 （沒有插補） 之間。</span><span class="sxs-lookup"><span data-stu-id="147e5-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="147e5-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>和<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>用來建立變數取決於值之間轉換<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="147e5-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="147e5-109">在下列範例中，動畫開始關閉變慢，但時間區段的結尾，以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="147e5-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="147e5-110">範例</span><span class="sxs-lookup"><span data-stu-id="147e5-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="147e5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="147e5-111">See Also</span></span>  
 [<span data-ttu-id="147e5-112">在立體場景中建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="147e5-112">Animate Camera Position and Direction in a 3D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [<span data-ttu-id="147e5-113">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="147e5-113">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
