---
title: 如何：使用腳本建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: a6cc8774c14d4b393b0d04822216c894e486ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>如何：使用腳本建立立體旋轉的動畫
下列範例示範如何進行時它"wobbles 」 所建立的動畫旋轉的 3D 物件<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>和<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>屬性<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件。 這<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件會指定旋轉轉換的 3D 物件，並因此動畫顯示其屬性建立 desire 旋轉效果。 分鏡腳本，內<xref:System.Windows.Media.Animation.DoubleAnimation>用來建立動畫<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>屬性中的，而<xref:System.Windows.Media.Animation.Vector3DAnimation>用來建立動畫<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>屬性。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 Rotation3DAnimation 建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [使用主要畫面格建立立體旋轉的動畫 (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
