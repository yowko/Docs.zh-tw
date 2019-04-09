---
title: HOW TO：使用主要畫面格建立物件的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0b2b517410c6cbc4f3deca13e5948c8de583fd3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177797"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>HOW TO：使用主要畫面格建立物件的動畫
此範例示範如何以動畫顯示物件，這在此範例中是<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項，使用主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別以動畫顯示色彩變更為<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項。 範例動畫會定期變成不同的背景筆刷。 這個動畫使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類別來建立三個不同的主要畫面格。 動畫會使用主要畫面格，以下列方式：  
  
1.  在第一次的第二個結束時，以動畫顯示的執行個體<xref:System.Windows.Media.LinearGradientBrush>類別。 本節的範例適用於線性漸層背景色彩，使色彩從黃色轉換為橙色為紅色。  
  
2.  在下一步 的第二個結束時，以動畫顯示的執行個體<xref:System.Windows.Media.RadialGradientBrush>類別。 本節的範例適用於放射狀漸層背景色彩，以便從白色到黑色藍色的色彩轉換。  
  
3.  在第三個第二個結束時，以動畫顯示的執行個體<xref:System.Windows.Media.DrawingBrush>類別。 本節的範例適用於在背景以棋盤式圖樣。  
  
4.  再次開始動畫，並且不斷重複。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 是唯一的類型，您可以搭配使用的主要畫面格<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別。 主要畫面格像<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>也就是在值中，建立突然的變更，在此範例中的色彩變更會突然發生。  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
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
