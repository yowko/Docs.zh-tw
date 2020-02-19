---
title: 如何：使用線形漸層繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 76c491632911c48db34d932ba3895278591378a5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452762"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>如何：使用線形漸層繪製區域
這個範例示範如何使用 <xref:System.Windows.Media.LinearGradientBrush> 類別，以線性漸層繪製區域。 在下列範例中，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 會以對角線線性漸層繪製，而此漸層會從黃色轉換成紅色到藍色，到淺綠色。  
  
## <a name="example"></a>範例  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![對角線線性漸層](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 若要建立水平線性漸層，請將 <xref:System.Windows.Media.LinearGradientBrush> 的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 變更為（0，0.5）和（1，0.5）。 在下列範例中，會以水平線性漸層繪製 <xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![水平線性漸層](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 若要建立垂直線性漸層，請將 <xref:System.Windows.Media.LinearGradientBrush> 的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 變更為（0.5，0）和（0.5，1）。 在下列範例中，會以垂直線性漸層繪製 <xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![垂直線性漸層](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
> 本主題中的範例會使用預設座標系統來設定起始點和結束點。 預設座標系統是相對於周框方塊：0表示周框方塊的0%，而1表示周框方塊的100%。 您可以藉由將 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> 屬性設為 <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>的值，來變更此座標系統。 絕對座標系統不會相對於週框方塊。 值會直接在本機空間中解譯。  
  
 如需其他範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。 如需漸層和其他類型之筆刷的詳細資訊，請參閱[使用純色和漸層繪製的色彩](painting-with-solid-colors-and-gradients-overview.md)。
