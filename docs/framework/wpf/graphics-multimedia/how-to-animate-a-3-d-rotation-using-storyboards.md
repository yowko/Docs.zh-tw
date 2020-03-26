---
title: 如何：使用分鏡腳本為 3D 旋轉設置動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112206"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a>如何：使用分鏡腳本為 3D 旋轉設置動畫
下面的示例演示如何通過對<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A><xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A><xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件的 和 屬性進行動畫處理，使其在"擺動"時旋轉。 此<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件指定 3D 物件的旋轉變換，因此對其屬性進行動畫處理可創建欲望旋轉效果。 在分鏡腳本中<xref:System.Windows.Media.Animation.DoubleAnimation>，用於為<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>屬性設置動畫，<xref:System.Windows.Media.Animation.Vector3DAnimation>同時用於為<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>屬性設置動畫。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [使用旋轉3D動畫為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [使用關鍵幀為 3D 旋轉設置動畫（旋轉3D動畫使用關鍵幀）](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3D 圖形概述](3-d-graphics-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
