---
title: 操作說明：使用主要畫面格建立色彩的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344741"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>操作說明：使用主要畫面格建立色彩的動畫
此示例演示如何使用關鍵幀對<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>動畫設置。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.SolidColorBrush>設置<xref:System.Windows.Media.SolidColorBrush.Color%2A>動畫。 這個動畫會以下列方式使用三個主要畫面格：  
  
1. 在前兩秒鐘中<xref:System.Windows.Media.Animation.LinearColorKeyFrame>，使用類的實例逐漸將顏色從綠色更改為紅色。 線性關鍵幀（<xref:System.Windows.Media.Animation.LinearColorKeyFrame>如在值之間創建平滑線性過渡）  
  
2. 在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>類的實例快速將顏色從紅色更改為黃色。 離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>如在值之間創建突然變化）表示，動畫的這一部分中的顏色變化會迅速發生，並且不微妙。  
  
3. 在最後兩秒鐘內<xref:System.Windows.Media.Animation.SplineColorKeyFrame>，使用類的實例再次更改顏色 - 這一次從黃色返回為綠色。 樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineColorKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。 在此範例中，色彩變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
