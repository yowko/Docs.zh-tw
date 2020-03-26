---
title: 如何：創建 3D 場景
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112098"
---
# <a name="how-to-create-a-3d-scene"></a>如何：創建 3D 場景
此示例演示如何創建看起來像已旋轉的平面紙張的 3D 物件。 A<xref:System.Windows.Controls.Viewport3D>與以下元件一起用於創建這個簡單的 3D 場景：  
  
- 使用 創建攝像機<xref:System.Windows.Media.Media3D.PerspectiveCamera>。 攝像機指定 3D 場景的哪些部分是可查看的。  
  
- 創建網格是為了使用<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>的屬性指定 3D 物件（紙張）的形狀。 <xref:System.Windows.Media.Media3D.GeometryModel3D>  
  
- 指定材質用於使用<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A><xref:System.Windows.Media.Media3D.GeometryModel3D>的屬性顯示在物件表面（此示例中的線性漸層）。  
  
- 創建一個光來使用<xref:System.Windows.Media.Media3D.DirectionalLight>在物件上發光。  
  
## <a name="example"></a>範例  
 下面的代碼顯示了如何在 XAML 中創建 3D 場景。  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>範例  
 下面的代碼演示如何在過程代碼中創建相同的 3D 場景。  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [3D 圖形概述](3-d-graphics-overview.md)
