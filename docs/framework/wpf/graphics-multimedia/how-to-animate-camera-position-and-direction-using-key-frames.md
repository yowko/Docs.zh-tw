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
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>如何：使用主要畫面格建立鏡頭位置和方向的動畫
在下面的示例中，<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>用於為 3D 場景中的位置<xref:System.Windows.Media.Media3D.PerspectiveCamera>設置動畫。 此外，<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>還用於為攝像機在 3D 場景中指向的方向設置動畫。 這兩個動畫都使用幾個關鍵幀來創建一系列動畫效果：  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame><xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>並用於在值之間創建平滑的線性插值。  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame><xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>並用於在值之間創建突然的"跳躍"（無插值）。  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>並<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>用於根據<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>屬性在值之間創建變數轉換。 在下面的示例中，動畫開始緩慢，但接近時段的末尾，速度呈指數級增長。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [在立體場景中建立鏡頭位置和方向的動畫](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [3D 圖形概述](3-d-graphics-overview.md)
