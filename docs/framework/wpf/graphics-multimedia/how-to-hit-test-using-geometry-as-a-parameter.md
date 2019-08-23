---
title: 作法：使用幾何作為參數進行點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923398"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>HOW TO：使用幾何作為參數進行點擊測試
這個範例示範如何使用<xref:System.Windows.Media.Geometry>作為點擊測試參數, 在視覺物件上執行點擊測試。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用<xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>來設定方法的點擊測試。 傳遞<xref:System.Windows.Point> <xref:System.Windows.Media.Geometry>至方法的值是用來建立物件, 以便擴充點擊測試的範圍。 `OnMouseDown`  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 的<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> <xref:System.Windows.Media.Geometry>屬性會提供使用作為點擊測試參數的點擊測試<xref:System.Windows.Media.GeometryHitTestResult>結果相關資訊。 下圖顯示點擊測試幾何 (藍色圓形) 和目標視覺物件呈現內容 (紅色矩形) 之間的關係。  
  
 ![此圖顯示用於點擊測試的 IntersectionDetail。](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 下列範例示範如何在<xref:System.Windows.Media.Geometry>將當做點擊測試參數使用時, 執行點擊測試回呼。 參數會轉換<xref:System.Windows.Media.GeometryHitTestResult>成, 以便<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>取得屬性的值。 `result` 屬性值可讓您判斷<xref:System.Windows.Media.Geometry>點擊測試參數是完全或部分包含在點擊測試目標的呈現內容中。 在此情況下，範例程式碼僅將點擊測試結果加入至完全包含在目標範圍內之視覺效果的清單中。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> 當<xref:System.Windows.Media.HitTestResult>交集詳細資料是<xref:System.Windows.Media.IntersectionDetail.Empty>時, 不應呼叫回呼。  
  
## <a name="see-also"></a>另請參閱

- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
- [對 Visual 中的幾何進行點擊測試](how-to-hit-test-geometry-in-a-visual.md)
