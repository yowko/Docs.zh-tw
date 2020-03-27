---
title: 如何：使用主要畫面格建立物件的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344710"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>如何：使用主要畫面格建立物件的動畫
此示例演示如何使用關鍵幀為物件設置動畫，在此示例中，物件是<xref:System.Windows.Controls.Page.Background%2A><xref:System.Windows.Controls.Page>控制項的屬性。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>為控制項<xref:System.Windows.Controls.Page.Background%2A>的屬性的顏色更改設置<xref:System.Windows.Controls.Page>動畫。 示例動畫會定期更改為不同的背景畫筆。 此動畫使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類創建三個不同的關鍵幀。 動畫使用關鍵幀的方式如下：  
  
1. 在第一秒結束時，為<xref:System.Windows.Media.LinearGradientBrush>類的實例設置動畫。 此示例的這一部分將線性漸層應用於背景顏色，以便顏色從黃色轉換為橙色轉換為紅色。  
  
2. 在下一秒結束時，為<xref:System.Windows.Media.RadialGradientBrush>類的實例設置動畫。 此示例的這一部分將徑向漸變應用於背景顏色，以便顏色從白色轉換為藍色轉換為黑色。  
  
3. 在第三秒結束時，為<xref:System.Windows.Media.DrawingBrush>類的實例設置動畫。 此示例的這一部分將棋盤圖案應用於背景。  
  
4. 動畫再次開始並無限期重複。  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>是可用於<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類的唯一類型的關鍵幀。 關鍵幀（<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>如創建值的突然更改）即此示例中的顏色更改突然發生。  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
