---
title: "如何：使用四元數建立立體旋轉的動畫 | Microsoft Docs"
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
  - "立體轉譯, 動畫, 使用四元數"
  - "動畫, 立體轉譯, 使用四元數"
  - "四元數"
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用四元數建立立體旋轉的動畫
這個範例顯示如何使用四元數建立 3\-D 物件的旋轉動畫。  
  
 下列程式碼顯示將 <xref:System.Windows.Media.Media3D.QuaternionRotation3D> 做為 <xref:System.Windows.Media.Media3D.RotateTransform3D> 之 <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> 屬性值的情形。  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 在下列程式碼中，<xref:System.Windows.Media.Media3D.QuaternionRotation3D> 的動畫是以 <xref:System.Windows.Media.Animation.Storyboard> 內的 <xref:System.Windows.Media.Animation.QuaternionAnimation> 建立。  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## 範例  
 下列程式碼顯示整個範例。  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [使用腳本建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)   
 [使用 Rotation3DAnimation 建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)