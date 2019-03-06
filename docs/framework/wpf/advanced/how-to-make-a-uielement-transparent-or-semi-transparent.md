---
title: HOW TO：將 UIElement 設為透明或半透明
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370523"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>HOW TO：將 UIElement 設為透明或半透明
此範例示範如何讓<xref:System.Windows.UIElement>透明或半透明。 若要透明或半透明，請將項目，您將其<xref:System.Windows.UIElement.Opacity%2A>屬性。 值為`0.0`使項目完全透明，而值為`1.0`讓項目完全不透明。 值為`0.5`讓項目 50%不透明，依此類推。 項目的<xref:System.Windows.UIElement.Opacity%2A>設為`1.0`預設。  
  
## <a name="example"></a>範例  
 下列範例會設定<xref:System.Windows.UIElement.Opacity%2A> 按鈕`0.25`，讓它和其內容 （在此情況下，按鈕的文字） 25%不透明。  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 如果項目的內容有它們自己<xref:System.Windows.UIElement.Opacity%2A>設定，這些值會乘以內含項目<xref:System.Windows.UIElement.Opacity%2A>。  
  
 下列範例會將按鈕的設定<xref:System.Windows.UIElement.Opacity%2A>要`0.25`，而<xref:System.Windows.UIElement.Opacity%2A>的<xref:System.Windows.Controls.Image>控制項中的按鈕，以包含與`0.5`。 如此一來，影像會出現 12.5%不透明：0.25 * 0.5 = 0.125.  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 若要控制的項目不透明度的另一個方法是設定的不透明度<xref:System.Windows.Media.Brush>繪製項目。 這種方法可讓您選擇性地改變的部分項目，不透明度，並提供效能優勢，透過使用項目的<xref:System.Windows.UIElement.Opacity%2A>屬性。 下列範例會設定<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>用來繪製按鈕<xref:System.Windows.Controls.Control.Background%2A>設定為`0.25`。 如此一來，筆刷的背景為 25%不透明的但其內容 （按鈕的文字） 會保持 100%不透明。  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 您也可以控制筆刷內的個別色彩不的透明度。 如需有關色彩和筆刷的詳細資訊，請參閱 <<c0> [ 使用純色和漸層概觀繪製](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。 如需示範如何以動畫顯示的項目不透明度的範例，請參閱[以動畫顯示的項目或筆刷的不透明度](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)。
