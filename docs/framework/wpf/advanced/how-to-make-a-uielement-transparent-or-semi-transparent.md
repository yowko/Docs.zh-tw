---
title: "如何：將 UIElement 設為透明或半透明 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "不透明度, UIElements"
  - "UIElements 的透明度"
  - "UIElements, 不透明度"
  - "UIElements, 透明"
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：將 UIElement 設為透明或半透明
本範例示範如何將 <xref:System.Windows.UIElement> 設定為透明或半透明。  若要將項目設為透明或半透明，請設定項目的 <xref:System.Windows.UIElement.Opacity%2A> 屬性。  值 `0.0` 可讓項目變成完全透明，而值 `1.0` 則可讓項目變成完成不透明。  值 `0.5` 可讓項目變成 50% 不透明，依此類推。  根據預設，項目的 <xref:System.Windows.UIElement.Opacity%2A> 會設定為 `1.0`。  
  
## 範例  
 下列範例會將按鈕的 <xref:System.Windows.UIElement.Opacity%2A> 設定為 `0.25`，使按鈕及其內容 \(在這個案例中就是按鈕文字\) 變成 25% 不透明。  
  
 [!code-xml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 如果項目的內容有自己的 <xref:System.Windows.UIElement.Opacity%2A> 設定，這些值就會與包含項目的 <xref:System.Windows.UIElement.Opacity%2A> 相乘。  
  
 下列範例會將按鈕的 <xref:System.Windows.UIElement.Opacity%2A> 設定為 `0.25`，並將按鈕內含之 <xref:System.Windows.Controls.Image> 控制項的 <xref:System.Windows.UIElement.Opacity%2A> 設定為 `0.5`。  因此，影像顯示的不透明度為 12.5%：0.25 \* 0.5 \= 0.125。  
  
 [!code-xml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 控制項目透明度的另一種方法是設定用來繪製項目的 <xref:System.Windows.Media.Brush> 透明度。  這種方法可以讓您選擇性地更改項目某些部分的不透明度，而且在效能上的優勢大於使用項目的 <xref:System.Windows.UIElement.Opacity%2A> 屬性。  下列範例會將用來繪製按鈕 <xref:System.Windows.Controls.Control.Background%2A> 之 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.Brush.Opacity%2A> 設定為 `0.25`。  因此，筆刷的背景不透明度為 25%，但其內容 \(按鈕的文字\) 仍維持 100% 的不透明度。  
  
 [!code-xml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 您也可以控制筆刷內個別色彩的不透明度。  如需色彩和筆刷的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  如需如何建立項目不透明度動畫的範例，請參閱 [建立項目或筆刷不透明效果的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)。