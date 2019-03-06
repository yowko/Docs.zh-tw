---
title: HOW TO：對文字套用動畫
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: e62c8288460206e7ebfbc18787bd9c2f2144a5bc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356958"
---
# <a name="how-to-apply-animations-to-text"></a>HOW TO：對文字套用動畫
動畫可以變更應用程式中文字的顯示和外觀。 下列範例會使用不同類型的動畫來影響中的文字顯示<xref:System.Windows.Controls.TextBlock>控制項。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫顯示文字區塊的寬度。 寬度值會在 10 秒的期間內從文字區塊的寬度變更為 0，然後回復寬度值並繼續進行。 這種動畫會建立擦去效果。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫顯示文字區塊的不透明度。 不透明度值會在 5 秒的期間內從 1.0 變更為 0，然後回復不透明度值並繼續進行。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 下圖顯示的效果<xref:System.Windows.Controls.TextBlock>變更它的不透明度從控制項`1.00`要`0.00`期間所定義的 5 秒間隔<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
 ![不透明度從 1.00 變更為 0.00 的文字](./media/fadedtext01.png "FadedText01")  
不透明度從 1.00 變更為 0.00 的文字  
  
 下列範例會使用<xref:System.Windows.Media.Animation.ColorAnimation>以動畫顯示文字區塊的前景色彩。 前景色彩值會在 5 秒的期間內從某種色彩變更為第二種色彩，然後回復色彩值並繼續進行。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>旋轉文字區塊。 文字區塊會在 20 秒的期間內執行完整旋轉，然後繼續重複進行旋轉。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>另請參閱
- [動畫概觀](../graphics-multimedia/animation-overview.md)
