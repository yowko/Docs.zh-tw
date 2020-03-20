---
title: 如何：對文字套用動畫
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174624"
---
# <a name="how-to-apply-animations-to-text"></a>如何：對文字套用動畫
動畫可以變更應用程式中文字的顯示和外觀。 以下示例使用不同類型的動畫來影響<xref:System.Windows.Controls.TextBlock>控制項中文本的顯示。  
  
## <a name="example"></a>範例  
 下面的示例使用<xref:System.Windows.Media.Animation.DoubleAnimation>為文字區塊的寬度設置動畫。 寬度值會在 10 秒的期間內從文字區塊的寬度變更為 0，然後回復寬度值並繼續進行。 這種動畫會建立擦去效果。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 下面的示例使用 動畫<xref:System.Windows.Media.Animation.DoubleAnimation>處理文字區塊的不動性。 不透明度值會在 5 秒的期間內從 1.0 變更為 0，然後回復不透明度值並繼續進行。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 下圖顯示了<xref:System.Windows.Controls.TextBlock>控制項在 定義的 5 秒間隔`1.00``0.00`內將其不恰當性更改為的效果。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>  
  
 ![文本將不一性從 1.00 更改為 0.00。](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 下面的示例使用<xref:System.Windows.Media.Animation.ColorAnimation>為文字區塊的前景顏色設置動畫。 前景色彩值會在 5 秒的期間內從某種色彩變更為第二種色彩，然後回復色彩值並繼續進行。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 下面的示例使用 旋轉<xref:System.Windows.Media.Animation.DoubleAnimation>文字區塊。 文字區塊會在 20 秒的期間內執行完整旋轉，然後繼續重複進行旋轉。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](../graphics-multimedia/animation-overview.md)
