---
title: 操作說明：使用主要畫面格建立大小變更的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344641"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>操作說明：使用主要畫面格建立大小變更的動畫
這個範例示範如何使用主要畫面格建立大小變更的動畫。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.ArcSegment>設置<xref:System.Windows.Media.ArcSegment.Size%2A>動畫。 這個動畫會以下列方式使用三個主要畫面格：  
  
1. 在動畫的前半秒，使用<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>類的實例逐漸增加圓弧的大小。線性關鍵幀（<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>如在值之間創建平滑線性過渡）  
  
2. 在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>類的實例突然增加圓弧的大小。離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>如在值之間創建突然跳轉），即大小更改突然發生，並且不微妙。  
  
3. 在最後兩秒鐘內<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>，使用類的實例來增加圓弧的大小。樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。 在此範例中，弧線的大小一開始會緩慢增加，然後在接近時間區段結尾時以指數方式增加。  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
