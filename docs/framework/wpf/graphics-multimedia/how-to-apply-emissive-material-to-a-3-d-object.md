---
title: 如何：將透射材料應用於 3D 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3D objects
- 3D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: bf32b41ec2410c01ad137ec0ca9311f7c2b70061
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112150"
---
# <a name="how-to-apply-emissive-material-to-a-3d-object"></a>如何：將透射材料應用於 3D 物件
下面的示例演示如何使用<xref:System.Windows.Media.Media3D.EmissiveMaterial>向等於 E 使材料畫筆顏色的現有材質添加顏色。 下面的代碼顯示<xref:System.Windows.Media.Media3D.DiffuseMaterial>並<xref:System.Windows.Media.Media3D.EmissiveMaterial>結合應用，以向 Diffuse 材料的外觀添加藍色。  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 在程式碼中：  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>範例  
 以下代碼在 XAML 中顯示整個示例。  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>範例  
 下面是過程代碼中的全部示例。  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [創建 3D 場景](how-to-create-a-3-d-scene.md)
- [3D 圖形概述](3-d-graphics-overview.md)
- [在 3D 場景中設置材質屬性的動畫](how-to-animate-material-properties-in-a-3-d-scene.md)
- [將材質應用於 3D 物件的正面和背面](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
