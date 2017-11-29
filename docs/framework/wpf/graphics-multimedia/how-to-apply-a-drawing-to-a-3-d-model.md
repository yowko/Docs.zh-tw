---
title: "如何：套用繪圖至立體模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>如何：套用繪圖至立體模型
這個範例示範如何使用<xref:System.Windows.Media.DrawingBrush>為<xref:System.Windows.Media.Media3D.Material>套用至[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。  
  
 下列程式碼定義<xref:System.Windows.Media.DrawingGroup>做內容<xref:System.Windows.Media.DrawingBrush>。  <xref:System.Windows.Media.DrawingBrush>設為<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>屬性<xref:System.Windows.Media.Media3D.DiffuseMaterial>套用至[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面。  
  
 **注意：**它通常會定義為資源，可以重複使用，並簡化您的程式碼的複雜物件及類似下方繪製的值。 請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)如需詳細資訊。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>範例  
 下列程式碼顯示完整的範例。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
