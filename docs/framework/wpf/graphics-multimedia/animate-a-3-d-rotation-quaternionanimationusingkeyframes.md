---
title: "如何：使用主要畫面格建立立體旋轉的動畫 (QuaternionAnimationUsingKeyFrames) | Microsoft Docs"
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
  - "立體轉譯, 動畫, 使用主要畫面格 (QuaternionAnimationUsingKeyFrames)"
  - "動畫, 立體轉譯, 使用主要畫面格 (QuaternionAnimationUsingKeyFrames)"
  - "主要畫面格, QuaternionAnimationUsingKeyFrames"
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用主要畫面格建立立體旋轉的動畫 (QuaternionAnimationUsingKeyFrames)
下列範例使用 <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> 來製作立體物件旋轉。  這個動畫會使用下列主要畫面格：  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> 用於在兩個值之間建立平滑的線性插補 \(Linear Interpolation\)。  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> 用於在值之間建立突然的「跳躍點」\(Jump\) \(沒有插補\)。  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> 用於根據 <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> 屬性，建立值之間的可變轉換。  在以下範例中，此部分的動畫一開始很緩慢，但接近時間區段的結尾時會呈等比級數加速。  
  
## 範例  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## 請參閱  
 [使用腳本建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)   
 [使用 Rotation3DAnimation 建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)   
 [使用四元數建立立體旋轉的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)   
 [使用主要畫面格建立立體旋轉的動畫 \(Rotation3DAnimationUsingKeyFrames\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)