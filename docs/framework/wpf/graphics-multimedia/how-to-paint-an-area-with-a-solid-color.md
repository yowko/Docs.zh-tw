---
title: 操作說明：使用純色繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 017c685139979ec3aa411be6e6b5fdf0e91657de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878440"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="8581c-102">操作說明：使用純色繪製區域</span><span class="sxs-lookup"><span data-stu-id="8581c-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="8581c-103">若要繪製區域使用純色繪製區域，您可以使用預先定義的系統筆刷，例如<xref:System.Windows.Media.Brushes.Red%2A>或<xref:System.Windows.Media.Brushes.Blue%2A>，或者您可以建立新<xref:System.Windows.Media.SolidColorBrush>，並說明其<xref:System.Windows.Media.SolidColorBrush.Color%2A>使用 alpha、 紅色、 綠色和藍色值。</span><span class="sxs-lookup"><span data-stu-id="8581c-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="8581c-104">在 XAML 中，您也可以使用十六進位標記法來以純色繪製區域。</span><span class="sxs-lookup"><span data-stu-id="8581c-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="8581c-105">下列範例所使用的是每一種方法來繪製<xref:System.Windows.Shapes.Rectangle>藍色。</span><span class="sxs-lookup"><span data-stu-id="8581c-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8581c-106">範例</span><span class="sxs-lookup"><span data-stu-id="8581c-106">Example</span></span>  
 <span data-ttu-id="8581c-107">**使用預先定義的筆刷**</span><span class="sxs-lookup"><span data-stu-id="8581c-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="8581c-108">在下列範例會使用預先定義的筆刷<xref:System.Windows.Media.Brushes.Blue%2A>將矩形繪製成藍色。</span><span class="sxs-lookup"><span data-stu-id="8581c-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="8581c-109">**使用十六進位標記法**</span><span class="sxs-lookup"><span data-stu-id="8581c-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="8581c-110">下一個範例會使用 8 位數的十六進位標記法將矩形繪製成藍色。</span><span class="sxs-lookup"><span data-stu-id="8581c-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="8581c-111">**使用 ARGB 值**</span><span class="sxs-lookup"><span data-stu-id="8581c-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="8581c-112">下一個範例會建立<xref:System.Windows.Media.SolidColorBrush>，並說明其<xref:System.Windows.Media.SolidColorBrush.Color%2A>藍色使用 ARGB 值。</span><span class="sxs-lookup"><span data-stu-id="8581c-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="8581c-113">如需其他描述色彩的方式，請參閱<xref:System.Windows.Media.Color>結構。</span><span class="sxs-lookup"><span data-stu-id="8581c-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="8581c-114">**相關主題**</span><span class="sxs-lookup"><span data-stu-id="8581c-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="8581c-115">如需詳細資訊<xref:System.Windows.Media.SolidColorBrush>和其他範例，請參閱[使用純色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)概觀。</span><span class="sxs-lookup"><span data-stu-id="8581c-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="8581c-116">此程式碼範例是針對提供之較大範例的一部分<xref:System.Windows.Media.SolidColorBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="8581c-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="8581c-117">如需完整的範例，請參閱 [Brush 範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="8581c-117">For the complete sample, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8581c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8581c-118">See Also</span></span>  
 <xref:System.Windows.Media.Brushes>
