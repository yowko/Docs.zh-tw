---
title: "如何：建立複雜格線 | Microsoft Docs"
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
  - "行事曆, 建立"
  - "Grid 控制項, 建立, 複雜格線"
  - "月曆, 建立"
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建立複雜格線
此範例顯示如何使用 <xref:System.Windows.Controls.Grid> 建立外觀與月曆類似的版面配置。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Controls.RowDefinition> 和 <xref:System.Windows.Controls.ColumnDefinition> 類別來定義 8 個資料列和 8 個資料行。  範例中也會一併使用 <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=fullName> 及 <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=fullName> 附加屬性與 <xref:System.Windows.Shapes.Rectangle> 項目，這些項目會填滿各種資料行和資料列的背景。  因為 <xref:System.Windows.Controls.Grid> 中的每個儲存格都可以包含多個項目 \(這是一個 <xref:System.Windows.Controls.Grid> 和 <xref:System.Windows.Documents.Table> 之間的基本差異\)，所以可以進行這項設計。  
  
 此範例會使用垂直漸層對資料行和資料列進行 <xref:System.Windows.Shapes.Shape.Fill%2A> 處理，以便提升視覺呈現的效果以及月曆的可讀性。  樣式經過特殊設計的 <xref:System.Windows.Controls.TextBlock> 項目可以表示特定日期與星期幾。  使用 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性以及該應用程式樣式所定義的對齊屬性，便可以在儲存格內以絕對位置放置項目 <xref:System.Windows.Controls.TextBlock>。  
  
 [!code-xml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Documents.TableCell>   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)