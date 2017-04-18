---
title: "如何：使用主要畫面格建立鏡頭位置和方向的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的鏡頭方向"
  - "動畫, 使用主要畫面格的鏡頭位置"
  - "鏡頭方向, 使用主要畫面格建立動畫"
  - "鏡頭位置, 使用主要畫面格建立動畫"
  - "主要畫面格, 建立鏡頭方向的動畫"
  - "主要畫面格, 建立鏡頭位置的動畫"
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用主要畫面格建立鏡頭位置和方向的動畫
下列範例中會使用 <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> 在 3D 場景中以 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 的位置建立動畫。  此外，還會在 3D 場景中使用 <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> 以相機所指的方向建立動畫。  這兩個動畫都使用數個主要畫面格來建立一系列的動畫效果：  
  
1.  使用 <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> 和 <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> 在值之間建立平滑的線性插補 \(Linear Interpolation\)。  
  
2.  使用 <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> 和 <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> 在值之間建立突然的「跳躍點」\(Jump\) \(沒有插補\)。  
  
3.  使用 <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> 和 <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>，在值之間建立視 <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> 屬性而定的可變轉換。  在下列範例中，動畫一開始很緩慢，接著當接近時間區段結尾時會以等比級數的速度加速。  
  
## 範例  
 [!code-xml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## 請參閱  
 [在立體場景中建立鏡頭位置和方向的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)