---
title: 如何：使用關鍵幀為 3D 旋轉設置動畫（四元動畫使用關鍵幀）
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112293"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="13536-102">如何：使用關鍵幀為 3D 旋轉設置動畫（四元動畫使用關鍵幀）</span><span class="sxs-lookup"><span data-stu-id="13536-102">How to: Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="13536-103">在下面的示例中，<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>用於使 3D 物件旋轉。</span><span class="sxs-lookup"><span data-stu-id="13536-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="13536-104">此動畫使用以下關鍵幀：</span><span class="sxs-lookup"><span data-stu-id="13536-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="13536-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>用於在值之間創建平滑的線性插值。</span><span class="sxs-lookup"><span data-stu-id="13536-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="13536-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>用於在值之間創建突然的"跳躍"（無插值）。</span><span class="sxs-lookup"><span data-stu-id="13536-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="13536-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>用於根據<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>屬性在值之間創建變數轉換。</span><span class="sxs-lookup"><span data-stu-id="13536-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="13536-108">在下面的示例中，動畫的這一部分開始緩慢，但接近時段的末尾，速度呈指數級增長。</span><span class="sxs-lookup"><span data-stu-id="13536-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13536-109">範例</span><span class="sxs-lookup"><span data-stu-id="13536-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="13536-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13536-110">See also</span></span>

- [<span data-ttu-id="13536-111">使用分鏡腳本為 3D 旋轉設置動畫</span><span class="sxs-lookup"><span data-stu-id="13536-111">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="13536-112">使用旋轉3D動畫為 3D 旋轉設置動畫</span><span class="sxs-lookup"><span data-stu-id="13536-112">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="13536-113">使用四元數為 3D 旋轉設置動畫</span><span class="sxs-lookup"><span data-stu-id="13536-113">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="13536-114">使用關鍵幀為 3D 旋轉設置動畫（旋轉3D動畫使用關鍵幀）</span><span class="sxs-lookup"><span data-stu-id="13536-114">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="13536-115">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="13536-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="13536-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="13536-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
