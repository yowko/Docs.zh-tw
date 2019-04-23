---
title: HOW TO：使用幾何作為參數進行點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 73420d6ae1386676ed900e91b3951df9e0934db8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100960"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>HOW TO：使用幾何作為參數進行點擊測試
此範例示範如何在視覺物件使用執行點擊的測試<xref:System.Windows.Media.Geometry>做為點擊測試參數。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定點擊的測試，使用<xref:System.Windows.Media.GeometryHitTestParameters>針對<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法。 <xref:System.Windows.Point>值傳遞給`OnMouseDown`方法來建立<xref:System.Windows.Media.Geometry>以延伸點擊測試的範圍的物件。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>的屬性<xref:System.Windows.Media.GeometryHitTestResult>提供的使用點擊測試結果的相關資訊<xref:System.Windows.Media.Geometry>做為點擊測試參數。 下圖顯示點擊測試幾何 (藍色圓形) 和目標視覺物件呈現內容 (紅色矩形) 之間的關係。  
  
 ![在點擊測試會顯示 IntersectionDetail 的圖表。](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 下列範例示範如何實作點擊的測試回呼時<xref:System.Windows.Media.Geometry>做為點擊的測試參數。 `result`參數會轉換成<xref:System.Windows.Media.GeometryHitTestResult>若要擷取的值<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>屬性。 屬性值可讓您判斷如果<xref:System.Windows.Media.Geometry>點擊的測試參數完全或部分包含在點擊的測試目標呈現內容。 在此情況下，範例程式碼僅將點擊測試結果加入至完全包含在目標範圍內之視覺效果的清單中。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult>交集詳細資料時，應該不會呼叫回呼<xref:System.Windows.Media.IntersectionDetail.Empty>。  
  
## <a name="see-also"></a>另請參閱

- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
- [對 Visual 中的幾何進行點擊測試](how-to-hit-test-geometry-in-a-visual.md)
