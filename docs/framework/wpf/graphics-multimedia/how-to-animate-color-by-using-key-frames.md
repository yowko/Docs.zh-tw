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
ms.openlocfilehash: cb09a54df3d99e05e89ec0f3d9f17b0e9fe78647
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501174"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>操作說明：使用主要畫面格建立色彩的動畫
此範例示範如何建立動畫<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>使用主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>屬性<xref:System.Windows.Media.SolidColorBrush>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在前的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.LinearColorKeyFrame>逐漸變更色彩從綠色到紅色的類別。 線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearColorKeyFrame>建立平滑的線性轉換值之間。  
  
2.  下一步 結束期間半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>類別，以快速地從紅色的色彩變更為黃色。 特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>突然之間建立變更的值，也就是，動畫的這個部分中的色彩變更很快就會完成，而不是微量。  
  
3.  在最後的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.SplineColorKeyFrame>再次變更色彩的類別，這次從黃色變回綠色。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineColorKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>屬性。 在此範例中，色彩變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
