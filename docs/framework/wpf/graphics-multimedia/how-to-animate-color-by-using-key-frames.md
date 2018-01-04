---
title: "操作說明：使用主要畫面格建立色彩的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c6b4dc6ee04b20f47599bad84dda4648da255ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-color-by-using-key-frames"></a>操作說明：使用主要畫面格建立色彩的動畫
此範例示範如何以動畫方式顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>所使用的主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>屬性<xref:System.Windows.Media.SolidColorBrush>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在第一個兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.LinearColorKeyFrame>類別來逐漸從綠色將色彩變更為紅色。 線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearColorKeyFrame>建立值之間的平順地線性轉換。  
  
2.  在下個結束半秒，會使用的執行個體<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>類別，以快速地從紅色色彩變更為黃色。 獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>建立突變之間的值，也就是，動畫的這個部分中的色彩變更發生快速，並不是難以察覺。  
  
3.  期間最後兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.SplineColorKeyFrame>再次變更色彩的類別，從黃色備份目前為綠色。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineColorKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>屬性。 在此範例中，色彩變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
