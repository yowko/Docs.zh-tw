---
title: HOW TO：使用單色繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: c85ba72c858d155f29875bb944824db1c44ffaab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086841"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="7c87a-102">HOW TO：使用單色繪製區域</span><span class="sxs-lookup"><span data-stu-id="7c87a-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="7c87a-103">若要繪製區域使用純色繪製區域，您可以使用預先定義的系統筆刷，例如<xref:System.Windows.Media.Brushes.Red%2A>或<xref:System.Windows.Media.Brushes.Blue%2A>，或者您可以建立新<xref:System.Windows.Media.SolidColorBrush>，並說明其<xref:System.Windows.Media.SolidColorBrush.Color%2A>使用 alpha、 紅色、 綠色和藍色值。</span><span class="sxs-lookup"><span data-stu-id="7c87a-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="7c87a-104">在 XAML 中，您也可以使用十六進位標記法來以純色繪製區域。</span><span class="sxs-lookup"><span data-stu-id="7c87a-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="7c87a-105">下列範例所使用的是每一種方法來繪製<xref:System.Windows.Shapes.Rectangle>藍色。</span><span class="sxs-lookup"><span data-stu-id="7c87a-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c87a-106">範例</span><span class="sxs-lookup"><span data-stu-id="7c87a-106">Example</span></span>  
 <span data-ttu-id="7c87a-107">**使用預先定義的筆刷**</span><span class="sxs-lookup"><span data-stu-id="7c87a-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="7c87a-108">在下列範例會使用預先定義的筆刷<xref:System.Windows.Media.Brushes.Blue%2A>將矩形繪製成藍色。</span><span class="sxs-lookup"><span data-stu-id="7c87a-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="7c87a-109">**使用十六進位標記法**</span><span class="sxs-lookup"><span data-stu-id="7c87a-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="7c87a-110">下一個範例會使用 8 位數的十六進位標記法將矩形繪製成藍色。</span><span class="sxs-lookup"><span data-stu-id="7c87a-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="7c87a-111">**使用 ARGB 值**</span><span class="sxs-lookup"><span data-stu-id="7c87a-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="7c87a-112">下一個範例會建立<xref:System.Windows.Media.SolidColorBrush>，並說明其<xref:System.Windows.Media.SolidColorBrush.Color%2A>藍色使用 ARGB 值。</span><span class="sxs-lookup"><span data-stu-id="7c87a-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="7c87a-113">如需其他描述色彩的方式，請參閱<xref:System.Windows.Media.Color>結構。</span><span class="sxs-lookup"><span data-stu-id="7c87a-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="7c87a-114">**相關主題**</span><span class="sxs-lookup"><span data-stu-id="7c87a-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="7c87a-115">如需詳細資訊<xref:System.Windows.Media.SolidColorBrush>和其他範例，請參閱[使用純色和漸層概觀繪製](painting-with-solid-colors-and-gradients-overview.md)概觀。</span><span class="sxs-lookup"><span data-stu-id="7c87a-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="7c87a-116">此程式碼範例是針對提供之較大範例的一部分<xref:System.Windows.Media.SolidColorBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="7c87a-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="7c87a-117">如需完整的範例，請參閱 [Brush 範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="7c87a-117">For the complete sample, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c87a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c87a-118">See also</span></span>

- <xref:System.Windows.Media.Brushes>
