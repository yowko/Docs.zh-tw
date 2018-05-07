---
title: 如何：使用主要畫面格建立物件的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 7dc49bc6b3f9156507cb821bfc32b269365b206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>如何：使用主要畫面格建立物件的動畫
這個範例示範如何建立物件，即在此範例中的<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項，使用主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別以動畫方式顯示色彩變更為<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項。 範例動畫會定期變成不同的背景筆刷。 這個動畫使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類別來建立三個不同的主要畫面格。 動畫會以下列方式使用的主要畫面格：  
  
1.  在第一次的第二個結尾，以動畫顯示的執行個體<xref:System.Windows.Media.LinearGradientBrush>類別。 本節的範例適用於線性漸層背景色彩，使色彩從黃色轉換為紅色的橙色。  
  
2.  在下一步的第二個結尾，以動畫顯示的執行個體<xref:System.Windows.Media.RadialGradientBrush>類別。 本節的範例套用於放射狀漸層的背景色彩，以便從為藍色為黑色的白色轉換的色彩。  
  
3.  在第三個第二個結尾，以動畫顯示的執行個體<xref:System.Windows.Media.DrawingBrush>類別。 本節的範例會套用至背景棋盤式圖樣。  
  
4.  動畫會重新開始計算，並且不斷重複。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 是您可以搭配使用的主要畫面格的唯一類型<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別。 主要畫面格像<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>也就是建立值 中的突變、 突然出現在此範例中的色彩變更。  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
