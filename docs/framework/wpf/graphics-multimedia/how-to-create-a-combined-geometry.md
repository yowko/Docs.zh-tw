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
# <a name="how-to-create-a-combined-geometry"></a>HOW TO：建立合併幾何
此範例示範如何合併幾何。 若要結合兩個幾何，使用<xref:System.Windows.Media.CombinedGeometry>物件。 設定其<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>並<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>屬性結合，並設定兩個幾何<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>屬性，決定如何幾何會結合在一起，以`Union`， `Intersect`， `Exclude`，或`Xor`.  
  
 若要建立兩個或多個幾何的複合幾何，請使用<xref:System.Windows.Media.GeometryGroup>。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義幾何合併模式`Exclude`。  兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![排除的結果合併模式](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
合併的幾何排除  
  
 在下列標記中，<xref:System.Windows.Media.CombinedGeometry>定義的合併模式`Intersect`。  兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![合併模式的交集結果](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
合併的幾何的交集  
  
 在下列標記中，<xref:System.Windows.Media.CombinedGeometry>定義的合併模式`Union`。  兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Union 合併模式的結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
合併的幾何的聯集  
  
 在下列標記中，<xref:System.Windows.Media.CombinedGeometry>定義的合併模式`Xor`。  兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Xor 合併的幾何
