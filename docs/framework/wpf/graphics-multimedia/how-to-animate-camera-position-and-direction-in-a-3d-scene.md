---
title: 如何：在立體場景中建立鏡頭位置和方向的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 429139da809a78474f4f6a082fb6e3c08c72d431
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>如何：在立體場景中建立鏡頭位置和方向的動畫
下列範例會示範如何建立動畫相機的位置和的方向指向 3D 場景中的動畫。 這是使用<xref:System.Windows.Media.Animation.Point3DAnimation>和<xref:System.Windows.Media.Animation.Vector3DAnimation>以動畫方式顯示<xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A>和<xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A>屬性分別<xref:System.Windows.Media.Media3D.PerspectiveCamera>。 若要變更以回應事件的視景的檢視，您可以使用像這樣的動畫。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [使用主要畫面格建立鏡頭位置和方向的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
