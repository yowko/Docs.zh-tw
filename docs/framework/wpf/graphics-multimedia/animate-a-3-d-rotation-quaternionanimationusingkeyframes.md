---
title: HOW TO：使用主要畫面格建立立體旋轉的動畫 (QuaternionAnimationUsingKeyFrames)
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 87176df26405a69cb2c3d63620def0575b750b52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338016"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>HOW TO：使用主要畫面格建立立體旋轉的動畫 (QuaternionAnimationUsingKeyFrames)
在下列範例中，<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>用來進行旋轉 3D 物件。 這個動畫會使用下列的主要畫面格：  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> 用來建立值之間的平滑的線性插補。  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> 用來建立突然 「 跳躍點 」 值 （沒有插補） 之間。  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> 用來建立變數轉換取決於值之間<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>屬性。 在下列範例中，動畫的這個部分很緩慢，但接近時間區段結尾開始，以指數方式加速。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [使用分鏡腳本建立立體旋轉的動畫](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [使用 Rotation3DAnimation 建立立體旋轉的動畫](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [使用四元數建立立體旋轉的動畫](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [使用主要畫面格建立立體旋轉的動畫 (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [立體圖形概觀](3-d-graphics-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
