---
title: 如何：使用主要畫面格建立鏡頭位置和方向的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112163"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="bff9b-102">如何：使用主要畫面格建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="bff9b-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="bff9b-103">在下面的示例中，<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>用於為 3D 場景中的位置<xref:System.Windows.Media.Media3D.PerspectiveCamera>設置動畫。</span><span class="sxs-lookup"><span data-stu-id="bff9b-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="bff9b-104">此外，<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>還用於為攝像機在 3D 場景中指向的方向設置動畫。</span><span class="sxs-lookup"><span data-stu-id="bff9b-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="bff9b-105">這兩個動畫都使用幾個關鍵幀來創建一系列動畫效果：</span><span class="sxs-lookup"><span data-stu-id="bff9b-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1. <span data-ttu-id="bff9b-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame><xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>並用於在值之間創建平滑的線性插值。</span><span class="sxs-lookup"><span data-stu-id="bff9b-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="bff9b-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame><xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>並用於在值之間創建突然的"跳躍"（無插值）。</span><span class="sxs-lookup"><span data-stu-id="bff9b-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="bff9b-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>並<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>用於根據<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>屬性在值之間創建變數轉換。</span><span class="sxs-lookup"><span data-stu-id="bff9b-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="bff9b-109">在下面的示例中，動畫開始緩慢，但接近時段的末尾，速度呈指數級增長。</span><span class="sxs-lookup"><span data-stu-id="bff9b-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bff9b-110">範例</span><span class="sxs-lookup"><span data-stu-id="bff9b-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bff9b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bff9b-111">See also</span></span>

- [<span data-ttu-id="bff9b-112">在立體場景中建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="bff9b-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="bff9b-113">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="bff9b-113">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
