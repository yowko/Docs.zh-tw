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
ms.workload: dotnet
ms.openlocfilehash: ee77da00604b7e4965cc376748606b6bd0e92ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a>如何：建立合併幾何
這個範例示範如何結合幾何。 若要結合兩個幾何，使用<xref:System.Windows.Media.CombinedGeometry>物件。 設定其<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>屬性結合，並設定兩個幾何<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>屬性，決定如何幾何會結合在一起，以`Union`， `Intersect`， `Exclude`，或`Xor`.  
  
 若要建立兩個或多個幾何的複合幾何，請使用<xref:System.Windows.Media.GeometryGroup>。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義幾何合併模式`Exclude`。  同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![排除的結果合併模式](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
合併的幾何排除  
  
 在下列標記<xref:System.Windows.Media.CombinedGeometry>定義合併模式`Intersect`。  同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![合併模式的交集結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
合併的幾何的交集  
  
 在下列標記<xref:System.Windows.Media.CombinedGeometry>定義合併模式`Union`。  同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Union 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
結合的幾何聯集  
  
 在下列標記<xref:System.Windows.Media.CombinedGeometry>定義合併模式`Xor`。  同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Xor 合併的幾何
