---
title: HOW TO：使用線形漸層繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: c48ff13811d784ecc7042b73b964a9e6f2d42a34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921880"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>HOW TO：使用線形漸層繪製區域
此範例示範如何使用<xref:System.Windows.Media.LinearGradientBrush>類別，以使用線形漸層繪製區域。 在下列範例中，<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>使用轉換從黃色到紅色變成藍色變成淡黃綠色對角線性漸層繪製。  
  
## <a name="example"></a>範例  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 下圖顯示先前範例所建立的漸層。  
  
 ![對角線性漸層](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 若要建立的水平的線性漸層，請變更<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>和<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的<xref:System.Windows.Media.LinearGradientBrush>到 (0,0.5) 和 (1,0.5)。 在下列範例中，<xref:System.Windows.Shapes.Rectangle>用於水平的線性漸層繪製。  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 下圖顯示先前範例所建立的漸層。  
  
 ![水平的線性漸層](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 若要建立垂直線性漸層，請變更<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>和<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的<xref:System.Windows.Media.LinearGradientBrush>到 (0.5,0) 和 (0.5,1)。 在下列範例中，<xref:System.Windows.Shapes.Rectangle>用於垂直線性漸層繪製。  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 下圖顯示先前範例所建立的漸層。  
  
 ![垂直線性漸層](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  本主題中的範例會使用預設座標系統來設定起始點和結束點。 預設座標系統是相對於週框方塊：0 表示 0%的週框方塊中，而 1 表示週框方塊的 100%。 您可以設定來變更這個座標系統<xref:System.Windows.Media.GradientBrush.MappingMode%2A>屬性設為值<xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>。 絕對座標系統不會相對於週框方塊。 值會直接在本機空間中解譯。  
  
 如需其他範例，請參閱 <<c0> [ 筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。 如需有關漸層和其他類型的筆刷的詳細資訊，請參閱[使用純色和漸層概觀繪製](painting-with-solid-colors-and-gradients-overview.md)。
