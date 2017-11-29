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
ms.openlocfilehash: 4cd857f7ce886095bcbe92ae57c350ce83bb5c7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="ee5ba-102">如何：將 RectangleGeometry 的邊角設為圓角</span><span class="sxs-lookup"><span data-stu-id="ee5ba-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="ee5ba-103">若要圓角<xref:System.Windows.Media.RectangleGeometry>，將其<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性的值小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="ee5ba-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="ee5ba-104">值愈大，愈矩形的圓角。</span><span class="sxs-lookup"><span data-stu-id="ee5ba-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee5ba-105">範例</span><span class="sxs-lookup"><span data-stu-id="ee5ba-105">Example</span></span>  
 <span data-ttu-id="ee5ba-106">下列範例示範數個<xref:System.Windows.Media.RectangleGeometry>物件具有不同<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="ee5ba-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="ee5ba-107"><xref:System.Windows.Media.RectangleGeometry>物件會使用顯示<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="ee5ba-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="ee5ba-108">![具有不同 RadiusX &#47; 的矩形RadiusY 設定](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="ee5ba-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="ee5ba-109">具有圓角矩形</span><span class="sxs-lookup"><span data-stu-id="ee5ba-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5ba-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee5ba-110">See Also</span></span>  
 [<span data-ttu-id="ee5ba-111">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="ee5ba-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="ee5ba-112">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="ee5ba-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="ee5ba-113">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="ee5ba-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
