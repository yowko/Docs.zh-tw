---
title: "如何：使用純色繪製區域 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "筆刷, 使用純色繪製"
  - "繪圖, 使用純色"
  - "純色, 繪製方式"
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用純色繪製區域
若要使用純色繪製區域，您可以使用預先定義的系統筆刷，例如 <xref:System.Windows.Media.Brushes.Red%2A> 或 <xref:System.Windows.Media.Brushes.Blue%2A>，或者您也可以建立新的 <xref:System.Windows.Media.SolidColorBrush>，並使用 Alpha 值、紅色值、綠色值和藍色值來描述其 <xref:System.Windows.Media.SolidColorBrush.Color%2A>。  在 XAML 中，您還可以利用十六進位標記法，使用純色來繪製區域。  
  
 下列範例將使用上述各項技巧將 <xref:System.Windows.Shapes.Rectangle> 繪製成藍色。  
  
## 範例  
 **使用預先定義的筆刷**  
  
 下列範例使用預先定義的筆刷 <xref:System.Windows.Media.Brushes.Blue%2A> 將矩形繪製成藍色。  
  
 [!code-xml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **使用十六進位標記法**  
  
 下一個範例使用 8 位數的十六進位標記法，將矩形繪製成藍色。  
  
 [!code-xml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **使用 ARGB 值**  
  
 下一個範例會建立 <xref:System.Windows.Media.SolidColorBrush>，並使用藍色的 ARGB 值描述它的 <xref:System.Windows.Media.SolidColorBrush.Color%2A>。  
  
 [!code-xml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 如需了解其他描述色彩的方法，請參閱 <xref:System.Windows.Media.Color>。  
  
 **相關主題**  
  
 如需 <xref:System.Windows.Media.SolidColorBrush> 的詳細資訊及其他範例，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
 這個程式碼範例是 <xref:System.Windows.Media.SolidColorBrush> 類別完整範例的一部分。  如需完整範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Brushes>