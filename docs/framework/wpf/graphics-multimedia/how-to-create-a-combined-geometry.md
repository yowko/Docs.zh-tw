---
title: HOW TO：建立合併幾何
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364784"
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="1540a-102">HOW TO：建立合併幾何</span><span class="sxs-lookup"><span data-stu-id="1540a-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="1540a-103">此範例示範如何合併幾何。</span><span class="sxs-lookup"><span data-stu-id="1540a-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="1540a-104">若要結合兩個幾何，使用<xref:System.Windows.Media.CombinedGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="1540a-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="1540a-105">設定其<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>並<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>屬性結合，並設定兩個幾何<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>屬性，決定如何幾何會結合在一起，以`Union`， `Intersect`， `Exclude`，或`Xor`.</span><span class="sxs-lookup"><span data-stu-id="1540a-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="1540a-106">若要建立兩個或多個幾何的複合幾何，請使用<xref:System.Windows.Media.GeometryGroup>。</span><span class="sxs-lookup"><span data-stu-id="1540a-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1540a-107">範例</span><span class="sxs-lookup"><span data-stu-id="1540a-107">Example</span></span>  
 <span data-ttu-id="1540a-108">在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義幾何合併模式`Exclude`。</span><span class="sxs-lookup"><span data-stu-id="1540a-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="1540a-109">兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。</span><span class="sxs-lookup"><span data-stu-id="1540a-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="1540a-110">![排除的結果合併模式](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="1540a-110">![Results of the Exclude combine mode](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="1540a-111">合併的幾何排除</span><span class="sxs-lookup"><span data-stu-id="1540a-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="1540a-112">在下列標記中，<xref:System.Windows.Media.CombinedGeometry>定義的合併模式`Intersect`。</span><span class="sxs-lookup"><span data-stu-id="1540a-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="1540a-113">兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。</span><span class="sxs-lookup"><span data-stu-id="1540a-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="1540a-114">![合併模式的交集結果](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="1540a-114">![Results of the Intersect combine mode](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="1540a-115">合併的幾何的交集</span><span class="sxs-lookup"><span data-stu-id="1540a-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="1540a-116">在下列標記中，<xref:System.Windows.Media.CombinedGeometry>定義的合併模式`Union`。</span><span class="sxs-lookup"><span data-stu-id="1540a-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="1540a-117">兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。</span><span class="sxs-lookup"><span data-stu-id="1540a-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="1540a-118">![Union 合併模式的結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="1540a-118">![Results of the Union combine mode](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="1540a-119">合併的幾何的聯集</span><span class="sxs-lookup"><span data-stu-id="1540a-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="1540a-120">在下列標記中，<xref:System.Windows.Media.CombinedGeometry>定義的合併模式`Xor`。</span><span class="sxs-lookup"><span data-stu-id="1540a-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="1540a-121">兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。</span><span class="sxs-lookup"><span data-stu-id="1540a-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="1540a-122">![Xor 合併模式的結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="1540a-122">![Results of the Xor combine mode](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="1540a-123">Xor 合併的幾何</span><span class="sxs-lookup"><span data-stu-id="1540a-123">Combined Geometry Xor</span></span>
