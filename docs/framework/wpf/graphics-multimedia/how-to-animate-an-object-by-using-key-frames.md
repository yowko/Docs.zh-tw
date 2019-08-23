---
title: 作法：使用主要畫面格建立物件的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933913"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>HOW TO：使用主要畫面格建立物件的動畫
這個範例示範如何使用主要畫面格, 以動畫顯示物件 (在<xref:System.Windows.Controls.Page.Background%2A>此範例中<xref:System.Windows.Controls.Page>為控制項的屬性)。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別, 以動畫顯示<xref:System.Windows.Controls.Page>控制項<xref:System.Windows.Controls.Page.Background%2A>屬性的色彩變更。 範例動畫會以固定間隔變更為不同的背景筆刷。 這個動畫會使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類別來建立三個不同的主要畫面格。 動畫會以下列方式使用主要畫面格:  
  
1. 在第一秒結束時, 會以動畫呈現<xref:System.Windows.Media.LinearGradientBrush>類別的實例。 範例的這個部分會將線性漸層套用至背景色彩, 讓色彩從黃色轉換成紅色。  
  
2. 在下一秒結束時, 會以動畫呈現<xref:System.Windows.Media.RadialGradientBrush>類別的實例。 範例的這個部分會將放射漸層套用至背景色彩, 讓色彩從白色轉換成黑色。  
  
3. 在第三秒結束時, 會以動畫呈現<xref:System.Windows.Media.DrawingBrush>類別的實例。 範例的這個部分會將棋盤圖樣套用到背景。  
  
4. 動畫會重新開始, 並無限期地重複。  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>是唯一可與<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別搭配使用的主要畫面格類型。 像<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>是在值中建立突然變更的主要畫面格 (也就是此範例中的色彩變更突然發生)。  
  
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
- [主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)
