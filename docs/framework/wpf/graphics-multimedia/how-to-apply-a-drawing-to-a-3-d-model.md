---
title: "如何：套用繪圖至立體模型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "立體模型, 將繪圖套用至"
  - "繪圖, 套用至立體模型"
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：套用繪圖至立體模型
這個範例顯示如何使用 <xref:System.Windows.Media.DrawingBrush>，做為套用至[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型的 <xref:System.Windows.Media.Media3D.Material>。  
  
 下列程式碼會將 <xref:System.Windows.Media.DrawingGroup> 定義為 <xref:System.Windows.Media.DrawingBrush> 的內容。  <xref:System.Windows.Media.DrawingBrush> 是設定為套用至[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面之 <xref:System.Windows.Media.Media3D.DiffuseMaterial> 的 <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> 屬性。  
  
 **注意：**通常最好是將複雜物件和值 \(例如下列繪圖\) 定義為資源，以供重複使用並簡化程式碼。  如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 [!code-xml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## 範例  
 下列程式碼顯示整個範例。  
  
 [!code-xml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## 請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)