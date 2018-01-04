---
title: "操作說明：使用幾何當做參數進行點擊測試"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b5c5bb47e3f435419bcf3c472f052260adec7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>操作說明：使用幾何當做參數進行點擊測試
這個範例示範如何執行點擊的測試視覺化的物件，使用<xref:System.Windows.Media.Geometry>作為點擊測試參數。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定使用點擊的測試<xref:System.Windows.Media.GeometryHitTestParameters>如<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法。 <xref:System.Windows.Point>值傳遞至`OnMouseDown`方法用來建立<xref:System.Windows.Media.Geometry>以展開的點擊測試範圍的物件。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>屬性<xref:System.Windows.Media.GeometryHitTestResult>提供資訊的使用點擊測試結果<xref:System.Windows.Media.Geometry>作為點擊測試參數。 下圖顯示點擊測試幾何 (藍色圓形) 和目標視覺物件呈現內容 (紅色矩形) 之間的關係。  
  
 ![圖表中使用之 IntersectionDetail 的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")  
點擊測試幾何和目標視覺物件之間的交集  
  
 下列範例示範如何實作點擊的測試回呼時<xref:System.Windows.Media.Geometry>作為點擊的測試參數。 `result`參數轉換成<xref:System.Windows.Media.GeometryHitTestResult>才能擷取的值<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>屬性。 屬性值可讓您判斷如果<xref:System.Windows.Media.Geometry>點擊的測試參數完全或部分包含在點擊的測試目標的呈現的內容。 在此情況下，範例程式碼僅將點擊測試結果加入至完全包含在目標範圍內之視覺效果的清單中。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult>交集詳細資料時，應該不會呼叫回呼<xref:System.Windows.Media.IntersectionDetail.Empty>。  
  
## <a name="see-also"></a>請參閱  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [對 Visual 中的幾何進行點擊測試](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
