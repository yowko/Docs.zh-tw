---
title: HOW TO：建立立體場景
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: a431b78993d197dac99f0b6e365823acb295f0b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611641"
---
# <a name="how-to-create-a-3-d-scene"></a>HOW TO：建立立體場景
此範例示範如何建立 3d 物件看起來像一般的工作表的已旋轉的紙張。 A<xref:System.Windows.Controls.Viewport3D>搭配下列元件用來建立這個簡單的 3d 場景：  
  
- 使用建立相機<xref:System.Windows.Media.Media3D.PerspectiveCamera>。 將觀景窗指定可檢視 3d 場景的哪個部分。  
  
- 網格會建立以指定的 3d 物件 （單張紙） 使用的形狀<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>。  
  
- 要顯示物件 （在此範例中的線性漸層） 使用的介面上指定材質<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>。  
  
- 光建立物件的使用平台<xref:System.Windows.Media.Media3D.DirectionalLight>。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何在 XAML 中的 3d 場景。  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>範例  
 下列程式碼示範如何在程序性程式碼中建立相同的 3d 場景。  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [立體圖形概觀](3-d-graphics-overview.md)
