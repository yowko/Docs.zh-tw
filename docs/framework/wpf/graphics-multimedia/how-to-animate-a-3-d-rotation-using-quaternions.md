---
title: HOW TO：使用四元數建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: d994ac2ae67fd366f27f123d5bd15f14d5ac7abe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183218"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a>HOW TO：使用四元數建立立體旋轉的動畫
此範例示範如何以動畫顯示 3d 物件使用四元數旋轉。  
  
 以下顯示的程式碼<xref:System.Windows.Media.Media3D.QuaternionRotation3D>做為值<xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>屬性<xref:System.Windows.Media.Media3D.RotateTransform3D>。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 這<xref:System.Windows.Media.Media3D.QuaternionRotation3D>以動畫顯示與<xref:System.Windows.Media.Animation.QuaternionAnimation>內<xref:System.Windows.Media.Animation.Storyboard>使用下列程式碼。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>範例  
 下列程式碼顯示整個範例。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [建立立體場景](how-to-create-a-3-d-scene.md)
- [立體圖形概觀](3-d-graphics-overview.md)
- [轉換概觀](transforms-overview.md)
- [使用分鏡腳本建立立體旋轉的動畫](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [使用 Rotation3DAnimation 建立立體旋轉的動畫](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
