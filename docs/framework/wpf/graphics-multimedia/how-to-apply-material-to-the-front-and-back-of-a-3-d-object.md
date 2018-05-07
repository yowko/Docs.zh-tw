---
title: 如何：對立體物件的前後套用材質
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 0ccf0aa045886f0731cd22ecdc8e14fa6af55fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>如何：對立體物件的前後套用材質
下列範例示範如何套用<xref:System.Windows.Media.Media3D.Material>前端並裝訂 3d 物件，並以動畫顯示的物件，以顯示物件的兩面。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>用於套用紅色<xref:System.Windows.Media.Brush>至物件的正面和<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>用於套用藍色<xref:System.Windows.Media.Brush>至物件的後端。 下列程式碼會顯示應用程式的資料物件：  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>範例  
 下列程式碼顯示完整的範例。  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [在立體場景中建立材質屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [將射出材質套用至立體物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
