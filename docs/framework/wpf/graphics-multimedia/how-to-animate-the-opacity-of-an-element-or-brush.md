---
title: HOW TO：建立元素或筆刷不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: f07138a0b68fff050133d477074571c60cd8651e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020188"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>HOW TO：建立元素或筆刷不透明效果的動畫
若要讓架構元素淡出畫面，您可以以動畫顯示其<xref:System.Windows.UIElement.Opacity%2A>屬性，或者您可以建立動畫<xref:System.Windows.Media.Brush.Opacity%2A>屬性<xref:System.Windows.Media.Brush>（或筆刷） 用來繪製它。 建立的項目不透明度動畫可讓和其子系淡出畫面，但以動畫顯示筆刷，用來繪製項目可讓您更謹慎選擇哪些項目的部分淡。 例如，您無法以動畫顯示用來繪製按鈕背景的筆刷的不透明度。 這會導致按鈕的背景淡出放大檢視，同時保留它的文字完全不透明。  
  
> [!NOTE]
>  建立動畫<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.Brush>透過以動畫顯示的效能優點<xref:System.Windows.UIElement.Opacity%2A>元素的屬性。  
  
 在下列範例中，兩個按鈕會使它們淡動畫效果。 第一個的不透明度<xref:System.Windows.Controls.Button>從以動畫顯示`1.0`要`0.0`透過<xref:System.Windows.Media.Animation.Timeline.Duration%2A>五秒。 第二個按鈕也以動畫顯示，但 SolidColorBrush 的不透明度會用來繪製其<xref:System.Windows.Controls.Control.Background%2A>動畫而不是整個按鈕的不透明度。 執行範例時，第一個按鈕完全淡，而第二個按鈕的背景淡。 其文字和框線保持完全不透明。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 此範例中，已省略的程式碼。 完整的範例也會示範如何以動畫顯示的不透明度<xref:System.Windows.Media.Color>內<xref:System.Windows.Media.LinearGradientBrush>。  如需完整的範例，請參閱[建立項目範例的不透明度動畫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation)。
