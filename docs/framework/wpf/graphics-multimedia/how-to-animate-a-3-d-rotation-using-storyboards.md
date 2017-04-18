---
title: "如何：使用腳本建立立體旋轉的動畫 | Microsoft Docs"
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
  - "立體轉譯, 動畫, 使用腳本"
  - "動畫, 立體轉譯, 使用腳本"
  - "分鏡腳本"
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用腳本建立立體旋轉的動畫
下列範例顯示如何以 <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> 物件的 <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> 和 <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> 屬性建立動畫，藉以建立一邊旋轉一邊搖擺的 3D 物件。  這個 <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> 物件會指定對 3D 物件進行旋轉轉換，並以其屬性建立符合所要旋轉效果的動畫。  在腳本內，<xref:System.Windows.Media.Animation.DoubleAnimation> 可用以建立 <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> 屬性的動畫，而 <xref:System.Windows.Media.Animation.Vector3DAnimation> 可用以建立 <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> 屬性的動畫。  
  
## 範例  
 [!code-xml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## 請參閱  
 [使用 Rotation3DAnimation 建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)   
 [使用主要畫面格建立立體旋轉的動畫 \(Rotation3DAnimationUsingKeyFrames\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)