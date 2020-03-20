---
title: 操作說明：使用純色繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849518"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>操作說明：使用純色繪製區域
要使用<xref:System.Windows.Media.Brushes.Red%2A>純色繪製區域，可以使用預定義的系統畫筆（如 或<xref:System.Windows.Media.Brushes.Blue%2A>，）或者可以使用 Alpha、紅色、綠色和<xref:System.Windows.Media.SolidColorBrush>藍色值創建新<xref:System.Windows.Media.SolidColorBrush.Color%2A>區域並描述其區域。 在 XAML 中，您也可以使用十六進位標記法來以純色繪製區域。  
  
 以下示例使用以下每種技術來繪製<xref:System.Windows.Shapes.Rectangle>藍色。  
  
## <a name="example"></a>範例  
 **使用預先定義的筆刷**  
  
 在下面的示例中，使用預定義的畫筆<xref:System.Windows.Media.Brushes.Blue%2A>繪製一個矩形藍色。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **使用十六進位標記法**  
  
 下一個範例會使用 8 位數的十六進位標記法將矩形繪製成藍色。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **使用 ARGB 值**  
  
 下一個示例創建<xref:System.Windows.Media.SolidColorBrush>和<xref:System.Windows.Media.SolidColorBrush.Color%2A>描述其使用顏色為藍色的 ARGB 值。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 有關描述顏色的其他方法，<xref:System.Windows.Media.Color>請參閱結構。  
  
 **相關主題**  
  
 有關相關資訊<xref:System.Windows.Media.SolidColorBrush>和其他示例，請參閱["具有純色和漸變的繪畫概述](painting-with-solid-colors-and-gradients-overview.md)"。  
  
 此代碼示例是為類提供的更大示例的<xref:System.Windows.Media.SolidColorBrush>一部分。 有關完整示例，請參閱[畫筆示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Brushes>
