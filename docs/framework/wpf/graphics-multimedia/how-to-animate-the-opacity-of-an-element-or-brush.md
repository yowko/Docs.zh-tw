---
title: 作法：建立元素或筆刷不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 2f18861eb18f81b631245d1d933b7acb1b3e0e42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950504"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>HOW TO：建立元素或筆刷不透明效果的動畫
若要讓架構元素淡入和移出畫面, 您可以建立其<xref:System.Windows.UIElement.Opacity%2A>屬性的動畫, 或是以<xref:System.Windows.Media.Brush.Opacity%2A>動畫顯示用<xref:System.Windows.Media.Brush>來繪製它之 (或筆刷) 的屬性。 以動畫顯示專案的不透明度會使其和子系淡入和移出視野, 但以動畫顯示用來繪製專案的筆刷, 可讓您更清楚地瞭解元素的哪個部分會淡化。 例如, 您可以建立用來繪製按鈕背景的筆刷不透明度的動畫。 這會導致按鈕的背景淡入和消失, 同時讓其文字完全不透明。  
  
> [!NOTE]
> <xref:System.Windows.UIElement.Opacity%2A>以<xref:System.Windows.Media.Brush.Opacity%2A> 動畫顯示,可讓您以動畫顯示專案屬性的效能優勢。<xref:System.Windows.Media.Brush>  
  
 在下列範例中, 兩個按鈕會以動畫顯示, 使其淡入和移出。 第一個<xref:System.Windows.Controls.Button>的不透明度會從`1.0`動畫顯示`0.0`為<xref:System.Windows.Media.Animation.Timeline.Duration%2A>五秒的。 第二個按鈕也會以動畫顯示, 但是用來繪製它<xref:System.Windows.Controls.Control.Background%2A>的 SolidColorBrush 不透明度會以動畫顯示, 而不是整個按鈕的不透明度。 執行此範例時, 第一個按鈕會完全淡入和移出視野, 而只有第二個按鈕的背景淡入和移出。 它的文字和框線會保持完全不透明。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 已省略此範例中的程式碼。 完整的範例也會示範如何以動畫顯示<xref:System.Windows.Media.Color> <xref:System.Windows.Media.LinearGradientBrush>中的不透明度。  如需完整範例, 請參閱[動畫不透明度的元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation)。
