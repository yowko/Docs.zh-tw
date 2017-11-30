---
title: "如何：建立合併幾何"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2be0471f27d26b145cc29847a08bf3bc3b1d51ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="9f169-102">如何：建立合併幾何</span><span class="sxs-lookup"><span data-stu-id="9f169-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="9f169-103">這個範例示範如何結合幾何。</span><span class="sxs-lookup"><span data-stu-id="9f169-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="9f169-104">若要結合兩個幾何，使用<xref:System.Windows.Media.CombinedGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="9f169-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="9f169-105">設定其<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>屬性結合，並設定兩個幾何<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>屬性，決定如何幾何會結合在一起，以`Union`， `Intersect`， `Exclude`，或`Xor`.</span><span class="sxs-lookup"><span data-stu-id="9f169-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="9f169-106">若要建立兩個或多個幾何的複合幾何，請使用<xref:System.Windows.Media.GeometryGroup>。</span><span class="sxs-lookup"><span data-stu-id="9f169-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f169-107">範例</span><span class="sxs-lookup"><span data-stu-id="9f169-107">Example</span></span>  
 <span data-ttu-id="9f169-108">在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義幾何合併模式`Exclude`。</span><span class="sxs-lookup"><span data-stu-id="9f169-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="9f169-109">同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。</span><span class="sxs-lookup"><span data-stu-id="9f169-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="9f169-110">![排除的結果合併模式](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="9f169-110">![Results of the Exclude combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="9f169-111">合併的幾何排除</span><span class="sxs-lookup"><span data-stu-id="9f169-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="9f169-112">在下列標記<xref:System.Windows.Media.CombinedGeometry>定義合併模式`Intersect`。</span><span class="sxs-lookup"><span data-stu-id="9f169-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="9f169-113">同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。</span><span class="sxs-lookup"><span data-stu-id="9f169-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="9f169-114">![合併模式的交集結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="9f169-114">![Results of the Intersect combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="9f169-115">合併的幾何的交集</span><span class="sxs-lookup"><span data-stu-id="9f169-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="9f169-116">在下列標記<xref:System.Windows.Media.CombinedGeometry>定義合併模式`Union`。</span><span class="sxs-lookup"><span data-stu-id="9f169-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="9f169-117">同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。</span><span class="sxs-lookup"><span data-stu-id="9f169-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="9f169-118">![Union 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="9f169-118">![Results of the Union combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="9f169-119">結合的幾何聯集</span><span class="sxs-lookup"><span data-stu-id="9f169-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="9f169-120">在下列標記<xref:System.Windows.Media.CombinedGeometry>定義合併模式`Xor`。</span><span class="sxs-lookup"><span data-stu-id="9f169-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="9f169-121">同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。</span><span class="sxs-lookup"><span data-stu-id="9f169-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="9f169-122">![Xor 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="9f169-122">![Results of the Xor combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="9f169-123">Xor 合併的幾何</span><span class="sxs-lookup"><span data-stu-id="9f169-123">Combined Geometry Xor</span></span>
