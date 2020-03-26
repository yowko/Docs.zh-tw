---
title: 如何：將材質應用於 3D 物件的正面和背面
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112137"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a>如何：將材質應用於 3D 物件的正面和背面
下面的示例演示如何將 應用於<xref:System.Windows.Media.Media3D.Material>3D 物件的正面和背面，並為物件設置動畫以顯示物件的兩側。 的屬性<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A><xref:System.Windows.Media.Media3D.GeometryModel3D><xref:System.Windows.Media.Brush>用於將紅色應用於物件的正面，<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>而 屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>用於將藍色<xref:System.Windows.Media.Brush>應用於物件的背面。 下面的代碼顯示了材料在物件中的應用：  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>範例  
 以下代碼顯示整個示例。  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [創建 3D 場景](how-to-create-a-3-d-scene.md)
- [3D 圖形概述](3-d-graphics-overview.md)
- [在 3D 場景中設置材質屬性的動畫](how-to-animate-material-properties-in-a-3-d-scene.md)
- [將透射材料應用於 3D 物件](how-to-apply-emissive-material-to-a-3-d-object.md)
