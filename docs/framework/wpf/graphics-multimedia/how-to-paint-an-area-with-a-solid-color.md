---
title: HOW TO：使用單色繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: c85ba72c858d155f29875bb944824db1c44ffaab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922625"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>HOW TO：使用單色繪製區域
若要繪製區域使用純色繪製區域，您可以使用預先定義的系統筆刷，例如<xref:System.Windows.Media.Brushes.Red%2A>或<xref:System.Windows.Media.Brushes.Blue%2A>，或者您可以建立新<xref:System.Windows.Media.SolidColorBrush>，並說明其<xref:System.Windows.Media.SolidColorBrush.Color%2A>使用 alpha、 紅色、 綠色和藍色值。 在 XAML 中，您也可以使用十六進位標記法來以純色繪製區域。  
  
 下列範例所使用的是每一種方法來繪製<xref:System.Windows.Shapes.Rectangle>藍色。  
  
## <a name="example"></a>範例  
 **使用預先定義的筆刷**  
  
 在下列範例會使用預先定義的筆刷<xref:System.Windows.Media.Brushes.Blue%2A>將矩形繪製成藍色。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **使用十六進位標記法**  
  
 下一個範例會使用 8 位數的十六進位標記法將矩形繪製成藍色。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **使用 ARGB 值**  
  
 下一個範例會建立<xref:System.Windows.Media.SolidColorBrush>，並說明其<xref:System.Windows.Media.SolidColorBrush.Color%2A>藍色使用 ARGB 值。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 如需其他描述色彩的方式，請參閱<xref:System.Windows.Media.Color>結構。  
  
 **相關主題**  
  
 如需詳細資訊<xref:System.Windows.Media.SolidColorBrush>和其他範例，請參閱[使用純色和漸層概觀繪製](painting-with-solid-colors-and-gradients-overview.md)概觀。  
  
 此程式碼範例是針對提供之較大範例的一部分<xref:System.Windows.Media.SolidColorBrush>類別。 如需完整的範例，請參閱 [Brush 範例](https://go.microsoft.com/fwlink/?LinkID=159973)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Brushes>
