---
title: "操作說明：使用主要畫面格建立雙精度浮點數的動畫"
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
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e87717f6e2691142efa54a7e363f1038f8b74c1b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>操作說明：使用主要畫面格建立雙精度浮點數的動畫
這個範例示範如何建立動畫的屬性值<xref:System.Double>所使用的主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會讓矩形橫越畫面移動。 此範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>套用至<xref:System.Windows.Shapes.Rectangle>。 這個不斷重複的動畫會以下列方式使用三個主要畫面格：  
  
1.  在第一個 3 秒鐘期間使用的執行個體<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>類別將沿著路徑的矩形穩定的資料從其起始位置移至 500 的位置。 線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>建立值之間的平順地線性轉換。  
  
2.  在第四個第二個結束時，會使用的執行個體<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>突然將矩形移至下一個位置的類別。 獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>建立值之間的突然跳躍點。 在此範例中，矩形位在起始位置，接著會突然出現在 500 位置。  
  
3.  在最後的兩秒中，使用 執行個體<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>類別，以將矩形移回其開始位置。 曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>屬性。 在此範例中，矩形一開始會緩慢移動，然後在接近時間區段結尾時以指數方式加速移動。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
 此範例的程式碼版本使用的其他動畫範例的一致性，<xref:System.Windows.Media.Animation.Storyboard>物件以套用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。 或者，套用程式碼中的單一動畫，時，更容易使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不要使用<xref:System.Windows.Media.Animation.Storyboard>。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
