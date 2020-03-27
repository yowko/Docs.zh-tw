---
title: 使用主要畫面格建立字串的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344676"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>使用主要畫面格建立字串的動畫
此示例演示如何使用關鍵幀為字串設置動畫，在此示例中，該字串是<xref:System.Windows.Controls.ContentControl.Content%2A><xref:System.Windows.Controls.Button>控制項的屬性。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Controls.Button>設置<xref:System.Windows.Controls.ContentControl.Content%2A>動畫。  
  
 此示例中的所有關鍵幀都使用類的實例，<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>因為使用關鍵幀創建的字串動畫只能使用離散關鍵幀。 離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>如在值之間創建突然跳轉），即動畫更改發生得很快，並且不是微妙的。  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
