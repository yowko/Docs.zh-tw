---
title: 如何：使用關鍵幀為 3D 旋轉設置動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112306"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a>如何：使用關鍵幀為 3D 旋轉設置動畫
在下面的示例中，<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>用於使 3D 物件旋轉，而其旋轉軸動畫會導致"擺動"。 此動畫使用以下關鍵幀：  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>用於在值之間創建平滑的線性插值。  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>用於在值之間創建突然的"跳躍"（無插值）。  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>用於根據<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>屬性在值之間創建變數轉換。 在下面的示例中，動畫的這一部分開始緩慢，但接近時段的末尾，速度呈指數級增長。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [3D 圖形概述](3-d-graphics-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [使用分鏡腳本為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [使用旋轉3D動畫為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [使用四元數為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [使用關鍵幀為 3D 旋轉設置動畫（四元動畫使用關鍵幀）](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
