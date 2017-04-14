---
title: "如何：使用幾何當做參數進行點擊測試 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Geometry 物件, 視覺物件的點擊測試"
  - "點擊測試, 對使用 Geometry 物件的視覺物件"
  - "視覺物件, 點擊測試"
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用幾何當做參數進行點擊測試
本範例示範如何使用 <xref:System.Windows.Media.Geometry> 做為點擊測試 \(Hit Test\) 參數，在視覺化物件上執行[點擊測試](GTMT)。  
  
## 範例  
 下列範例顯示如何使用 <xref:System.Windows.Media.GeometryHitTestParameters>，為 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 方法設定點擊測試。  傳遞至 `OnMouseDown` 方法的 <xref:System.Windows.Point> 值可用來建立 <xref:System.Windows.Media.Geometry> 物件，以便擴展點擊測試的範圍。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult> 的 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> 屬性會提供將 <xref:System.Windows.Media.Geometry> 當成點擊測試參數之點擊測試的相關結果資訊。  下圖顯示點擊測試幾何圖形 \(藍色圓形\) 和目標視覺化物件所呈現內容 \(紅色正方形\) 之間的關係。  
  
 ![在點擊測試中使用之 IntersectionDetail 的圖表](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")  
點擊測試幾何圖形和目標視覺化物件之間的交集  
  
 下列範例顯示如何在使用 <xref:System.Windows.Media.Geometry> 當做點擊測試參數時實作點擊測試回呼 \(Callback\)。  `result` 參數會轉換為 <xref:System.Windows.Media.GeometryHitTestResult>，以便擷取 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> 屬性的值。  這個屬性值可以讓您判斷 <xref:System.Windows.Media.Geometry> 點擊測試參數是全部還是部分包含在點擊測試目標的呈現內容裡。  在這個案例中，範例程式碼只會將點擊測試結果，加入完全包含在目標界限內的視覺效果清單中。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  當交集詳細資料是 <xref:System.Windows.Media.IntersectionDetail> 時，就不應該呼叫 <xref:System.Windows.Media.HitTestResult> 回呼。  
  
## 請參閱  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [對 Visual 中的幾何進行點擊測試](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)