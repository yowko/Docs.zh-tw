---
title: HOW TO：使用主要畫面格建立框線粗細的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 101fd077bf125faadbd9a0186c2282e4b20ee78f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301785"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>HOW TO：使用主要畫面格建立框線粗細的動畫
此範例示範如何建立動畫<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1. 在前半秒，期間使用的執行個體<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>類別來逐漸增加的框線粗細。 此範例會使用<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>建立平滑的線性增加值之間。  
  
2. 在下一步結尾半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>突然增加的框線粗細的類別。 特定主要畫面格，例如衍生自<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>建立突然跳躍點之間的值，也就是為動畫的移動不穩定。  
  
3. 在最後的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>類別，以減少框線的粗細。 曲線主要畫面格，例如衍生自<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>屬性。 在此主要畫面格中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)
- [建立 BorderThickness 值的動畫](../controls/how-to-animate-a-borderthickness-value.md)
