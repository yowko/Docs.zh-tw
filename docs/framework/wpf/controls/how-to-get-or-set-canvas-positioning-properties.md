---
title: "如何：取得或設定 Canvas 定位屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Canvas 控制項, 設定定位屬性"
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：取得或設定 Canvas 定位屬性
本範例示範如何使用 <xref:System.Windows.Controls.Canvas> 項目的定位方法來放置子內容。  本範例使用 <xref:System.Windows.Controls.ListBoxItem> 中的內容來代表定位值，並將值轉換為 <xref:System.Double> 的執行個體，這個執行個體是定位時必要的引數。  接著使用 <xref:System.Windows.Controls.Canvas.GetLeft%2A> 方法將值轉換回字串，並且在 <xref:System.Windows.Controls.TextBlock> 項目中顯示為文字。  
  
## 範例  
 下列範例會建立具有 11 個可選取 <xref:System.Windows.Controls.ListBoxItem> 項目的 <xref:System.Windows.Controls.ListBox> 項目。  <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件會觸發 `ChangeLeft` 自訂方法，後續的程式碼區塊會定義這個方法。  
  
 每個 <xref:System.Windows.Controls.ListBoxItem> 都分別表示一個 <xref:System.Double> 值，這是 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Canvas.SetLeft%2A> 方法接受的其中一個引數。  為了要使用 <xref:System.Windows.Controls.ListBoxItem> 表示 <xref:System.Double> 的執行個體，您必須先將 <xref:System.Windows.Controls.ListBoxItem> 轉換為正確的資料型別。  
  
 [!code-xml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 當使用者變更 <xref:System.Windows.Controls.ListBox> 選項時，它會叫用 `ChangeLeft` 自訂方法。  這個方法會將 <xref:System.Windows.Controls.ListBoxItem> 傳送給 <xref:System.Windows.LengthConverter> 物件，此物件再將 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 轉換成 <xref:System.Double> 的執行個體 \(請注意，這個值已經藉由使用 <xref:System.Windows.Controls.Control.ToString%2A> 方法轉換成 <xref:System.String>\)。  然後這個值會傳送回 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Canvas.SetLeft%2A> 和 <xref:System.Windows.Controls.Canvas.GetLeft%2A> 方法，以變更 `text1` 物件的位置。  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.ListBoxItem>   
 <xref:System.Windows.LengthConverter>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)