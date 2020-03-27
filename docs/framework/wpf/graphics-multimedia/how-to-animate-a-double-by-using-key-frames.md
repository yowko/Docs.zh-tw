---
title: 操作說明：使用主要畫面格建立雙精度浮點數的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344947"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>操作說明：使用主要畫面格建立雙精度浮點數的動畫
此示例演示如何使用關鍵幀對 獲取 的屬性<xref:System.Double>的值設置動畫。  
  
## <a name="example"></a>範例  
 下列範例會讓矩形橫越畫面移動。 該示例使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>類為應用於<xref:System.Windows.Media.TranslateTransform.X%2A>的屬性<xref:System.Windows.Media.TranslateTransform>設置動畫<xref:System.Windows.Shapes.Rectangle>。 這個不斷重複的動畫會以下列方式使用三個主要畫面格：  
  
1. 在前三秒內，使用<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>類的實例以穩定速率沿路徑移動矩形，從起始位置移動到 500 位置。 線性關鍵幀（<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>如在值之間創建平滑線性過渡）  
  
2. 在第四秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>類的實例突然將矩形移動到下一個位置。 離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>如在值之間創建突然跳轉） 在此範例中，矩形位在起始位置，接著會突然出現在 500 位置。  
  
3. 在最後兩秒鐘中，使用類的<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>實例將矩形移回其起始位置。 樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。 在此範例中，矩形一開始會緩慢移動，然後在接近時間區段結尾時以指數方式加速移動。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
 為了與其他動畫示例保持一致，此示例的代碼版本使用<xref:System.Windows.Media.Animation.Storyboard>物件來應用 。 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 或者，在代碼中應用單個動畫時，使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法而不是 使用 更簡單。 <xref:System.Windows.Media.Animation.Storyboard> 例如，請參閱[在不使用分鏡腳本的情況下為屬性設置動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
