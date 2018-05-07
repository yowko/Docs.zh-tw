---
title: 如何：使用主要畫面格建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 085b2da20410d53fce6099131bf07249bde3209c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a>如何：使用主要畫面格建立立體旋轉的動畫
在下列範例中，<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>用來進行時其軸的旋轉動畫導致"微微"旋轉的 3D 物件。 這個動畫會使用下列的主要畫面格：  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> 用來建立值之間的順暢、 線性插補。  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> 用來建立突然"跳躍點 」 值 （沒有插補） 之間。  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> 用來建立變數取決於值之間轉換<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>屬性。 在下列範例中，動畫這部分很緩慢但時間區段的結尾開始，加速以等比級數。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [使用分鏡腳本建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [使用 Rotation3DAnimation 建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [使用四元數建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [使用主要畫面格建立立體旋轉的動畫 (QuaternionAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
