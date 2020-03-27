---
title: 如何：使用主要畫面格建立布林值的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 35704996dcf21fe463169dc13572941bcd8fbad1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344948"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a>如何：使用主要畫面格建立布林值的動畫
此示例演示如何使用關鍵幀為<xref:System.Windows.Controls.Button>控制項的布林屬性值設置動畫。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>為控制項<xref:System.Windows.UIElement.IsEnabled%2A>的屬性設置<xref:System.Windows.Controls.Button>動畫。 此示例中的所有關鍵幀都使用類的<xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>實例。 離散的關鍵幀，<xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>如在值之間創建突然跳轉，也就是說，動畫的移動是抖動的。  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
