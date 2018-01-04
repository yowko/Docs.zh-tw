---
title: "操作說明：使用主要畫面格建立框線粗細的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f255ff38ec7ee79f02a0cd40a3f0143c36e1c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>操作說明：使用主要畫面格建立框線粗細的動畫
此範例示範如何以動畫方式顯示<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在第一個半秒，會使用的執行個體<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>類別來逐漸增加框線的粗細。 此範例會使用<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>建立平滑的線性增加值之間。  
  
2.  在下一個結尾半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>類別以突然增加框線的粗細。 特定的主要畫面格，例如衍生自<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>建立突然跳躍點之間的值，也就是為動畫移動不穩定。  
  
3.  在最後的兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>類別，以減少框線的粗細。 曲線主要畫面格一樣衍生自<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>屬性。 在此主要畫面格中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [建立 BorderThickness 值的動畫](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
