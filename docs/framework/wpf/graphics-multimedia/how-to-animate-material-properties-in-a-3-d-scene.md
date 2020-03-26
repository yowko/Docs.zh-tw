---
title: 如何：在 3D 場景中設置材質屬性的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112189"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a>如何：在 3D 場景中設置材質屬性的動畫
此示例演示如何為應用於 3D<xref:System.Windows.Media.Brush.Opacity%2A>模型的屬性<xref:System.Windows.Media.Media3D.Material>設置動畫。  
  
 以下代碼示例將<xref:System.Windows.Media.LinearGradientBrush>用作<xref:System.Windows.Media.Media3D.Material>應用於 3D 物件的定義。  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 使用<xref:System.Windows.Media.Brush.Opacity%2A><xref:System.Windows.Media.LinearGradientBrush>下面的代碼示例對此的屬性進行動畫處理。  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>範例  
 以下代碼顯示整個示例。  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [創建 3D 場景](how-to-create-a-3-d-scene.md)
- [3D 圖形概述](3-d-graphics-overview.md)
