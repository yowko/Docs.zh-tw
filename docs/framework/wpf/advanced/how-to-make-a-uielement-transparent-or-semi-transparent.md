---
title: "如何：將 UIElement 設為透明或半透明"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec35ae2e064acf78d1165f64ce8c9e34b153299d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>如何：將 UIElement 設為透明或半透明
這個範例示範如何讓<xref:System.Windows.UIElement>透明或半透明。 請讓元素透明或半透明效果，您將設定其<xref:System.Windows.UIElement.Opacity%2A>屬性。 值為`0.0`完全透明，而值為類型建立項目`1.0`完全不透明類型建立項目。 值為`0.5`類型建立項目 50%不透明，依此類推。 項目的<xref:System.Windows.UIElement.Opacity%2A>設`1.0`預設。  
  
## <a name="example"></a>範例  
 下列範例會設定<xref:System.Windows.UIElement.Opacity%2A>的按鈕`0.25`，讓它和其內容 （在此情況下，按鈕的文字） 25%不透明。  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 如果項目的內容有其自己<xref:System.Windows.UIElement.Opacity%2A>設定，這些值會乘以內含項目<xref:System.Windows.UIElement.Opacity%2A>。  
  
 下列範例會設定按鈕的<xref:System.Windows.UIElement.Opacity%2A>至`0.25`，而<xref:System.Windows.UIElement.Opacity%2A>的<xref:System.Windows.Controls.Image>控制項中的按鈕，以包含與`0.5`。 如此一來，此影像隨即顯示 12.5%不透明： 0.25 * 0.5 = 0.125。  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 若要控制的項目不透明度的另一個方法是設定的不透明度<xref:System.Windows.Media.Brush>繪製項目。 這種方法可讓您選擇性地變更的部分項目的不透明度，並提供效能優勢，透過使用項目的<xref:System.Windows.UIElement.Opacity%2A>屬性。 下列範例會設定<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>用來繪製按鈕的<xref:System.Windows.Controls.Control.Background%2A>設`0.25`。 如此一來，背景的筆刷為 25%不透明，但其內容 （按鈕的文字） 保持 100%不透明。  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 您也可以控制筆刷內的個別色彩的不的透明度。 如需有關色彩和筆刷的詳細資訊，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。 如需顯示如何建立動畫項目的不透明度的範例，請參閱[以動畫顯示的項目或筆刷的不透明度](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)。
