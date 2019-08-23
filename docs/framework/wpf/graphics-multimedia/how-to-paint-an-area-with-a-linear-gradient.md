---
title: 作法：使用線形漸層繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916169"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>HOW TO：使用線形漸層繪製區域
這個範例顯示如何使用<xref:System.Windows.Media.LinearGradientBrush>類別, 以線性漸層繪製區域。 在下列範例中, <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>的會以對角線線性漸層繪製, 而此漸層會從黃色轉換成紅色到藍色, 到酸綠色。  
  
## <a name="example"></a>範例  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![對角線線性]漸層(./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 若要建立水平線性漸層, 請<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>將<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的和<xref:System.Windows.Media.LinearGradientBrush>變更為 (0, 0.5) 和 (1, 0.5)。 在下列範例中, <xref:System.Windows.Shapes.Rectangle>會以水平線性漸層繪製。  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![水平線性]漸層(./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 若要建立垂直線性漸層, 請<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>將<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的和<xref:System.Windows.Media.LinearGradientBrush>變更為 (0.5, 0) 和 (0.5, 1)。 在下列範例中, <xref:System.Windows.Shapes.Rectangle>會以垂直線性漸層繪製。  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 下圖顯示上一個範例所建立的漸層。  
  
 ![垂直線性]漸層(./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
> 本主題中的範例會使用預設座標系統來設定起始點和結束點。 預設座標系統是相對於周框方塊:0 表示週框方塊的 0%，1 表示週框方塊的 100%。 您可以藉由將<xref:System.Windows.Media.GradientBrush.MappingMode%2A>屬性設定為值<xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>來變更此座標系統。 絕對座標系統不會相對於週框方塊。 值會直接在本機空間中解譯。  
  
 如需其他範例, 請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。 如需漸層和其他類型之筆刷的詳細資訊, 請參閱[使用純色和漸層繪製的色彩](painting-with-solid-colors-and-gradients-overview.md)。
