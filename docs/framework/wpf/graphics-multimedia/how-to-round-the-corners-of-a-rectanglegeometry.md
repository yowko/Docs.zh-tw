---
title: HOW TO：將 RectangleGeometry 的邊角設為圓角
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089129"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="9c2d6-102">HOW TO：將 RectangleGeometry 的邊角設為圓角</span><span class="sxs-lookup"><span data-stu-id="9c2d6-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="9c2d6-103">要四捨五入的邊角<xref:System.Windows.Media.RectangleGeometry>，將其<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性小於或等於零的值。</span><span class="sxs-lookup"><span data-stu-id="9c2d6-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="9c2d6-104">值愈大，愈矩形邊角。</span><span class="sxs-lookup"><span data-stu-id="9c2d6-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c2d6-105">範例</span><span class="sxs-lookup"><span data-stu-id="9c2d6-105">Example</span></span>  
 <span data-ttu-id="9c2d6-106">下列範例將示範數個<xref:System.Windows.Media.RectangleGeometry>具有不同的物件<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="9c2d6-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="9c2d6-107"><xref:System.Windows.Media.RectangleGeometry>物件會顯示使用<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="9c2d6-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="9c2d6-108">![具有不同 RadiusX 的矩形&#47;RadiusY 設定](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="9c2d6-108">![Rectangles with different RadiusX&#47;RadiusY settings](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="9c2d6-109">具有圓角矩形</span><span class="sxs-lookup"><span data-stu-id="9c2d6-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2d6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c2d6-110">See also</span></span>

- [<span data-ttu-id="9c2d6-111">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="9c2d6-111">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="9c2d6-112">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="9c2d6-112">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="9c2d6-113">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="9c2d6-113">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
