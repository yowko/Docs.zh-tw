---
title: "操作說明：使用純色繪製區域"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cde7f7df5089806ffb3235393eacc855d137ee51
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="d3138-102">操作說明：使用純色繪製區域</span><span class="sxs-lookup"><span data-stu-id="d3138-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="d3138-103">若要繪製用純色區域，您可以使用預先定義的系統筆刷，例如<xref:System.Windows.Media.Brushes.Red%2A>或<xref:System.Windows.Media.Brushes.Blue%2A>，或者您可以建立新<xref:System.Windows.Media.SolidColorBrush>並描述其<xref:System.Windows.Media.SolidColorBrush.Color%2A>使用 alpha、 紅色、 綠色和藍色值。</span><span class="sxs-lookup"><span data-stu-id="d3138-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="d3138-104">在 XAML 中，您也可以使用十六進位標記法來以純色繪製區域。</span><span class="sxs-lookup"><span data-stu-id="d3138-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="d3138-105">下列範例會使用兩種技巧來繪製<xref:System.Windows.Shapes.Rectangle>藍色。</span><span class="sxs-lookup"><span data-stu-id="d3138-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3138-106">範例</span><span class="sxs-lookup"><span data-stu-id="d3138-106">Example</span></span>  
 <span data-ttu-id="d3138-107">**使用預先定義的筆刷**</span><span class="sxs-lookup"><span data-stu-id="d3138-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="d3138-108">在下列範例會使用預先定義的筆刷<xref:System.Windows.Media.Brushes.Blue%2A>來繪製矩形藍色。</span><span class="sxs-lookup"><span data-stu-id="d3138-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="d3138-109">**使用十六進位標記法**</span><span class="sxs-lookup"><span data-stu-id="d3138-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="d3138-110">下一個範例會使用 8 位數的十六進位標記法將矩形繪製成藍色。</span><span class="sxs-lookup"><span data-stu-id="d3138-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="d3138-111">**使用 ARGB 值**</span><span class="sxs-lookup"><span data-stu-id="d3138-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="d3138-112">下一個範例會建立<xref:System.Windows.Media.SolidColorBrush>，並說明其<xref:System.Windows.Media.SolidColorBrush.Color%2A>使用 ARGB 色彩藍色值。</span><span class="sxs-lookup"><span data-stu-id="d3138-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="d3138-113">如需描述色彩的其他方式，請參閱<xref:System.Windows.Media.Color>結構。</span><span class="sxs-lookup"><span data-stu-id="d3138-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="d3138-114">**相關主題**</span><span class="sxs-lookup"><span data-stu-id="d3138-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="d3138-115">如需有關<xref:System.Windows.Media.SolidColorBrush>和其他範例，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)概觀。</span><span class="sxs-lookup"><span data-stu-id="d3138-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="d3138-116">這個程式碼範例是針對所提供之較大範例的一部分<xref:System.Windows.Media.SolidColorBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="d3138-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="d3138-117">如需完整的範例，請參閱 [Brush 範例](http://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="d3138-117">For the complete sample, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3138-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3138-118">See Also</span></span>  
 <xref:System.Windows.Media.Brushes>
