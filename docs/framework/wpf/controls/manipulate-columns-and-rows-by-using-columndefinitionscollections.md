---
title: "如何：使用 ColumnDefinitionsCollections 和 RowDefinitionsCollections 管理資料行和資料列 | Microsoft Docs"
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
  - "類別, ColumnDefinitionCollection"
  - "類別, RowDefinitionCollection"
  - "ColumnDefinitionCollection 類別"
  - "控制項, Grid 類別"
  - "Grid 控制項, ColumnDefinitionCollection 類別"
  - "Grid 控制項, RowDefinitionCollection 類別"
  - "RowDefinitionCollection 類別"
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用 ColumnDefinitionsCollections 和 RowDefinitionsCollections 管理資料行和資料列
這個範例說明如何使用 <xref:System.Windows.Controls.ColumnDefinitionCollection> 及 <xref:System.Windows.Controls.RowDefinitionCollection> 類別中的方法，以執行如新增、清除或計算資料列或資料行內容等動作。  例如，您可以 <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>、<xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A> 或 <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> 包含在 <xref:System.Windows.Controls.ColumnDefinition> 或 <xref:System.Windows.Controls.RowDefinition> 中的項目。  
  
## 範例  
 下列範例會建立一個 <xref:System.Windows.Controls.Grid> 項目，且 <xref:System.Windows.FrameworkElement.Name%2A> 是 `grid1`。  <xref:System.Windows.Controls.Grid> 內含一個 <xref:System.Windows.Controls.StackPanel> 會保留 <xref:System.Windows.Controls.Button> 項目，而每一個項目都是由不同的收集方法所控制。  當您按一下 <xref:System.Windows.Controls.Button>，會啟動程式碼後置 \(Code\-Behind\) 檔案中的方法呼叫。  
  
 [!code-xml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 這個範例會定義一連串的自訂方法，每一個都對應於[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案中的一個 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  有幾種方式可以變更 <xref:System.Windows.Controls.Grid> 中的資料行和資料列數目 \(包括新增或移除資料列和資料行\)，以及計算資料列和資料行的總數。  如果要避免 <xref:System.ArgumentOutOfRangeException> 和 <xref:System.ArgumentException> 的例外狀況，您可以使用 <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> 方法所提供的錯誤檢查功能。  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Controls.ColumnDefinitionCollection>   
 <xref:System.Windows.Controls.RowDefinitionCollection>