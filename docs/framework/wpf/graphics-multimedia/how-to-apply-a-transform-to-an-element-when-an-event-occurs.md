---
title: HOW TO：在事件發生時套用轉換至項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 3862ffcb8e0dcabd2de67c495204470ac9fa6c14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726386"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>HOW TO：在事件發生時套用轉換至項目
此範例示範如何套用<xref:System.Windows.Media.ScaleTransform>事件發生時。 這裡所示範的概念，與您用來套用其他類型轉換的概念相同。 如需可用的轉換類型的詳細資訊，請參閱<xref:System.Windows.Media.Transform>類別或[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。  
  
 您可以透過下列兩種方式其中之一，將轉換套用至元素：  
  
-   如果您這樣做*未*希望轉換影響版面配置，請使用<xref:System.Windows.UIElement.RenderTransform%2A>項目的屬性。  
  
-   如果您希望轉換影響版面配置，使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>項目的屬性。  
  
 下列範例會套用<xref:System.Windows.Media.ScaleTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>按鈕的屬性。 當滑鼠移至按鈕，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>並<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>的屬性<xref:System.Windows.Media.ScaleTransform>設定為`2`，這會使按鈕變得越來越大。 當滑鼠移動按鈕，關閉<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>並<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>設定為`1`，這會使按鈕回到其原始大小。  
  
## <a name="example"></a>範例  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
- [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
