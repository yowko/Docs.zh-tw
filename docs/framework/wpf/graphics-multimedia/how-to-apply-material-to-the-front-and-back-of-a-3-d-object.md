---
title: HOW TO：對立體物件的前後套用材質
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 16f30e3a880d7dcc943a9583ba0f04c4bd682827
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652029"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>HOW TO：對立體物件的前後套用材質
下列範例示範如何套用<xref:System.Windows.Media.Media3D.Material>前面和背面的 3d 物件，並建立要顯示物件的兩邊的物件的動畫。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>可用來套用紅色<xref:System.Windows.Media.Brush>至物件的正面和<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>可用來套用藍色<xref:System.Windows.Media.Brush>到後端的物件。 下列程式碼顯示將材質套用至物件：  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>範例  
 下列程式碼顯示整個範例。  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱
- [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [在立體場景中建立材質屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)
- [將射出材質套用至立體物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
