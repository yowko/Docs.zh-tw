---
title: "如何：將 RectangleGeometry 的邊角設為圓角"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92a51b3c610d3755583f8a39314f45d3980ee1bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="0f972-102">如何：將 RectangleGeometry 的邊角設為圓角</span><span class="sxs-lookup"><span data-stu-id="0f972-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="0f972-103">若要圓角<xref:System.Windows.Media.RectangleGeometry>，將其<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性的值小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="0f972-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="0f972-104">值愈大，愈矩形的圓角。</span><span class="sxs-lookup"><span data-stu-id="0f972-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f972-105">範例</span><span class="sxs-lookup"><span data-stu-id="0f972-105">Example</span></span>  
 <span data-ttu-id="0f972-106">下列範例示範數個<xref:System.Windows.Media.RectangleGeometry>物件具有不同<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="0f972-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="0f972-107"><xref:System.Windows.Media.RectangleGeometry>物件會使用顯示<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="0f972-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="0f972-108">![具有不同 RadiusX &#47; 的矩形RadiusY 設定](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="0f972-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="0f972-109">具有圓角矩形</span><span class="sxs-lookup"><span data-stu-id="0f972-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f972-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f972-110">See Also</span></span>  
 [<span data-ttu-id="0f972-111">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="0f972-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="0f972-112">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="0f972-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="0f972-113">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="0f972-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
