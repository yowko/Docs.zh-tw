---
title: "如何：使用線形漸層繪製區域 | Microsoft Docs"
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
  - "筆刷, 使用線形漸層繪製"
  - "線形漸層, 繪製方式"
  - "繪圖, 使用線形漸層"
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用線形漸層繪製區域
本範例示範如何使用 <xref:System.Windows.Media.LinearGradientBrush> 類別以線形漸層繪製區域。  在下列範例中，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 會以對角線形漸層繪製，從黃色逐漸變成紅色，再變成藍色，最後變成淡黃綠色。  
  
## 範例  
 [!code-xml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![對角線性漸層](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.png "graphicsmm\_DiagonalLGB")  
  
 若要建立水平線形漸層，請將 <xref:System.Windows.Media.LinearGradientBrush> 的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 變更為 \(0,0.5\) 和 \(1,0.5\)。  在下列範例中，<xref:System.Windows.Shapes.Rectangle> 會以水平線形漸層繪製。  
  
 [!code-xml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![水平線性漸層](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.png "graphicsmm\_HorizontalLGB")  
  
 若要建立垂直線形漸層，請將 <xref:System.Windows.Media.LinearGradientBrush> 的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 變更為 \(0.5,0\) 和 \(0.5,1\)。  在下列範例中，<xref:System.Windows.Shapes.Rectangle> 會以垂直線形漸層繪製。  
  
 [!code-xml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![垂直線性漸層](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.png "graphicsmm\_VerticalLGB")  
  
> [!NOTE]
>  本主題中的範例會使用預設座標系統設定起始點和結束點。  預設座標系統與週框方塊有關：0 表示週框方塊的 0%，而 1 表示週框方塊的 100%。  您可以藉由將 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> 屬性設為值 <xref:System.Windows.Media.BrushMappingMode?displayProperty=fullName>，變更這個座標系統。  絕對座標系統不會相對於週框方塊。  值會直接在本機空間中解譯。  
  
 如需其他範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  如需漸層和其他筆刷類型的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。