---
title: 如何：建立項目或筆刷不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: a45bf0344c10e1214aa5218e25e9bd9a87d5ea60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>如何：建立項目或筆刷不透明效果的動畫
若要讓架構項目的淡入和移出檢視，您可以動畫顯示其<xref:System.Windows.UIElement.Opacity%2A>屬性，或可以動畫顯示<xref:System.Windows.Media.Brush.Opacity%2A>屬性<xref:System.Windows.Media.Brush>（或筆刷） 用來繪製它。 建立動畫項目的不透明度和其子系淡入和移出檢視，但是建立動畫的筆刷用來繪製項目可讓您更具選擇性的相關項目的部份淡出。 例如，您可以動畫顯示用來繪製按鈕的背景筆刷的不透明度。 這會導致按鈕的背景，淡入和移出檢視，同時保留它的文字完全不透明。  
  
> [!NOTE]
>  建立動畫<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.Brush>透過建立動畫的效能優點<xref:System.Windows.UIElement.Opacity%2A>某個項目的屬性。  
  
 在下列範例中，兩個按鈕被動畫，讓它們進入和離開檢視淡出。 第一個的不透明度<xref:System.Windows.Controls.Button>動畫從`1.0`至`0.0`透過<xref:System.Windows.Media.Animation.Timeline.Duration%2A>五秒。 第二個按鈕也會顯示動畫，但是 SolidColorBrush 的不透明度用來繪製其<xref:System.Windows.Controls.Control.Background%2A>動畫而不是整個按鈕的不透明度。 執行範例時，第一個按鈕完全淡進入和離開檢視，而第二個按鈕的背景會檢視。 其文字和框線保持完全不透明的。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 這個範例中省略了程式碼。 完整的範例也會示範如何建立動畫的不透明度<xref:System.Windows.Media.Color>內<xref:System.Windows.Media.LinearGradientBrush>。  如需完整的範例，請參閱[動畫項目範例的不透明度](http://go.microsoft.com/fwlink/?LinkID=159968)。
