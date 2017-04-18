---
title: "如何：建立立體轉譯動畫 | Microsoft Docs"
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
  - "立體轉譯, 動畫"
  - "動畫, 立體轉譯"
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立立體轉譯動畫
本主題示範如何建立在[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型上設定的平移轉換動畫。  
  
 下列程式碼顯示如何將 <xref:System.Windows.Media.Media3D.TranslateTransform3D> 物件應用在 <xref:System.Windows.Media.Media3D.GeometryModel3D> 的 <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> 屬性上。  
  
 [!code-xml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 此 <xref:System.Windows.Media.Media3D.TranslateTransform3D> 物件的 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> 屬性會使用下列程式碼建立動畫。  
  
 [!code-xml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## 範例  
 下列程式碼顯示整個範例。  
  
 [!code-xml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)