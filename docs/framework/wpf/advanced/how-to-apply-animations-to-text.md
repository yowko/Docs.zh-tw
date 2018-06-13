---
title: 如何：對文字套用動畫
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56a12ca915cc320619a094df38d118eabf202734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545434"
---
# <a name="how-to-apply-animations-to-text"></a>如何：對文字套用動畫
動畫可以變更應用程式中文字的顯示和外觀。 下列範例會使用不同類型的動畫來影響的文字顯示<xref:System.Windows.Controls.TextBlock>控制項。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫方式顯示的文字區塊的寬度。 寬度值會在 10 秒的期間內從文字區塊的寬度變更為 0，然後回復寬度值並繼續進行。 這種動畫會建立擦去效果。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫方式顯示的文字區塊的不透明度。 不透明度值會在 5 秒的期間內從 1.0 變更為 0，然後回復不透明度值並繼續進行。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 下圖顯示的效果<xref:System.Windows.Controls.TextBlock>控制項變更其透明度從`1.00`至`0.00`期間所定義的 5 秒間隔<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
 ![文字不透明度從 1.00 變更為 0.00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
不透明度從 1.00 變更為 0.00 的文字  
  
 下列範例會使用<xref:System.Windows.Media.Animation.ColorAnimation>以動畫方式顯示的文字區塊的前景色彩。 前景色彩值會在 5 秒的期間內從某種色彩變更為第二種色彩，然後回復色彩值並繼續進行。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>旋轉文字區塊。 文字區塊會在 20 秒的期間內執行完整旋轉，然後繼續重複進行旋轉。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
