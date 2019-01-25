---
title: HOW TO：使用腳本建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 0e5e0b4e2b991b15ff7a49da65bfe96485e66fcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589801"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>HOW TO：使用腳本建立立體旋轉的動畫
下列範例示範如何進行旋轉時它 「 wobbles 」 以動畫顯示 3D 物件<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>並<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>的屬性<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件。 這<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件會指定旋轉轉換的 3D 物件，並因此以動畫顯示其屬性建立的渴望旋轉的效果。 分鏡腳本，內<xref:System.Windows.Media.Animation.DoubleAnimation>用來建立動畫<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>屬性時<xref:System.Windows.Media.Animation.Vector3DAnimation>用來以動畫顯示<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>屬性。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱
- [使用 Rotation3DAnimation 建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [使用主要畫面格建立立體旋轉的動畫 (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)
- [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
