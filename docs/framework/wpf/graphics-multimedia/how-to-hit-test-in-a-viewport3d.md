---
title: "如何：Viewport3D 中的點擊測試 | Microsoft Docs"
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
  - "立體視覺效果, 點擊測試"
  - "點擊測試, 立體視覺效果"
  - "Viewport3D"
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：Viewport3D 中的點擊測試
本範例顯示如何對 <xref:System.Windows.Controls.Viewport3D> 中的 3D 視覺物件進行點擊測試。  
  
 因為 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 會傳回 2D 和 3D 資訊，所以可以逐一查看測試結果以只讀取 3D 結果。  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 下列程式碼中的 <xref:System.Windows.Media.HitTestResultBehavior> 決定點擊測試結果的處理方式。  `UpdateResultInfo` 和 `UpdateMaterial` 是在本機上定義的方法。  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## 請參閱  
 [立體點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159959)