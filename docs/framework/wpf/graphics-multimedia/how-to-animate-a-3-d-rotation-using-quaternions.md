---
title: 如何：使用四元數為 3D 旋轉設置動畫
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112241"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a>如何：使用四元數為 3D 旋轉設置動畫
此示例演示如何使用四元數為 3D 物件的旋轉設置動畫。  
  
 下面的代碼顯示了用作<xref:System.Windows.Media.Media3D.QuaternionRotation3D>屬性的值。 <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> <xref:System.Windows.Media.Media3D.RotateTransform3D>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 使用<xref:System.Windows.Media.Media3D.QuaternionRotation3D>下面的代碼在<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.QuaternionAnimation>中使用 動畫。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>範例  
 以下代碼顯示整個示例。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [創建 3D 場景](how-to-create-a-3-d-scene.md)
- [3D 圖形概述](3-d-graphics-overview.md)
- [轉換概觀](transforms-overview.md)
- [使用分鏡腳本為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [使用旋轉3D動畫為 3D 旋轉設置動畫](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
