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
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>如何：使用關鍵幀為 3D 旋轉設置動畫（四元動畫使用關鍵幀）
在下面的示例中，<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>用於使 3D 物件旋轉。 此動畫使用以下關鍵幀：  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>用於在值之間創建平滑的線性插值。  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>用於在值之間創建突然的"跳躍"（無插值）。  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>用於根據<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>屬性在值之間創建變數轉換。 在下面的示例中，動畫的這一部分開始緩慢，但接近時段的末尾，速度呈指數級增長。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [使用分鏡腳本為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [使用旋轉3D動畫為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [使用四元數為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [使用關鍵幀為 3D 旋轉設置動畫（旋轉3D動畫使用關鍵幀）](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3D 圖形概述](3-d-graphics-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
