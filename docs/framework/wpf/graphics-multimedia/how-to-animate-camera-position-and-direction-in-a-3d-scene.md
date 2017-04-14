---
title: "如何：在立體場景中建立鏡頭位置和方向的動畫 | Microsoft Docs"
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
  - "立體場景, 建立鏡頭方向的動畫"
  - "立體場景, 建立鏡頭位置的動畫"
  - "動畫, 立體場景中的鏡頭方向"
  - "動畫, 立體場景中的鏡頭位置"
  - "鏡頭方向, 在立體場景中建立動畫"
  - "鏡頭位置, 在立體場景中建立動畫"
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：在立體場景中建立鏡頭位置和方向的動畫
下列範例顯示如何在立體場景中建立鏡頭位置和其所指方向的動畫。  這是透過分別對 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 的 <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> 和 <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> 屬性使用 <xref:System.Windows.Media.Animation.Point3DAnimation> 和 <xref:System.Windows.Media.Animation.Vector3DAnimation> 建立動畫來達成。  您可以使用像這樣的動畫，變更觀看者的視景以回應某個事件。  
  
## 範例  
 [!code-xml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>   
 <xref:System.Windows.Media.Animation.Point3DAnimation>   
 [使用主要畫面格建立鏡頭位置和方向的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)