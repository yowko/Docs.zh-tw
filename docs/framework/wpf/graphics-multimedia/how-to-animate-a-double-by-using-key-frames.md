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
ms.openlocfilehash: 67466bbb5fd7e7a46c312e14666c23048bf43d80
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521212"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>操作說明：使用主要畫面格建立雙精度浮點數的動畫
此範例示範如何以動畫顯示採用屬性的值<xref:System.Double>使用主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會讓矩形橫越畫面移動。 此範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>套用至<xref:System.Windows.Shapes.Rectangle>。 這個不斷重複的動畫會以下列方式使用三個主要畫面格：  
  
1.  在前三秒內，會使用的執行個體<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>類別將矩形沿著路徑以穩定速率的資料從其起始位置移動到 500 位置。 線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>建立平滑的線性轉換值之間。  
  
2.  在第四秒結束時，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>突然將矩形移動到下一個位置的類別。 特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>建立突然跳躍點之間的值。 在此範例中，矩形位在起始位置，接著會突然出現在 500 位置。  
  
3.  在最後兩秒，使用的執行個體<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>類別來將矩形移回起始位置。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>屬性。 在此範例中，矩形一開始會緩慢移動，然後在接近時間區段結尾時以指數方式加速移動。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
 為了和其他動畫範例保持一致，使用此範例中的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>物件，要套用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。 或者，套用單一動畫的程式碼中，時，使用的工作變得更容易<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不是使用<xref:System.Windows.Media.Animation.Storyboard>。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
