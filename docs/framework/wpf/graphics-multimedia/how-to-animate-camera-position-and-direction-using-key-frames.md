---
title: "如何：使用主要畫面格建立鏡頭位置和方向的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbac99770b5cbb7dacb0468e1a892956fda6b79c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>如何：使用主要畫面格建立鏡頭位置和方向的動畫
在下列範例中，<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>用來建立動畫的位置<xref:System.Windows.Media.Media3D.PerspectiveCamera>3D 場景中。 此外，<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>會相機指向的 3D 場景方向的動畫。 這兩個動畫使用數個主要畫面格來建立一系列的動畫效果：  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>和<xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>用來建立值之間的順暢、 線性插補。  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>和<xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>用來建立突然"跳躍點 」 值 （沒有插補） 之間。  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>和<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>用來建立變數取決於值之間轉換<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>屬性。 在下列範例中，動畫開始關閉變慢，但時間區段的結尾，以指數方式加速。  
  
## <a name="example"></a>範例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [在立體場景中建立鏡頭位置和方向的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
