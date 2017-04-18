---
title: "如何：透過 Inlines 屬性管理非固定格式內容項目 | Microsoft Docs"
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
  - "文件, 透過 Inlines 屬性管理非固定格式內容項目"
  - "非固定格式內容項目, 透過 Inlines 屬性管理"
  - "Inlines 屬性, 管理非固定格式內容項目"
  - "屬性, Inlines, 管理非固定格式內容項目"
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：透過 Inlines 屬性管理非固定格式內容項目
這些範例示範可以在內嵌 \(Inline\) 的非固定格式內容項目上 \(和這類項目的容器，如 <xref:System.Windows.Controls.TextBlock>\)，透過 **Inlines** 屬性執行的幾個較常見的作業。  這個屬性用於加入和移除 <xref:System.Windows.Documents.InlineCollection> 中的項目。  具有 **Inlines** 屬性的非固定格式內容項目包括：  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 雖然這些範例中都是使用 <xref:System.Windows.Documents.Span> 做為非固定格式內容項目，但這些方法也適用於裝載 <xref:System.Windows.Documents.InlineCollection> 集合的所有項目或控制項。  
  
## 範例  
 下列範例會建立新的 <xref:System.Windows.Documents.Span> 物件，然後使用 **Add** 方法加入兩個文字執行做為 <xref:System.Windows.Documents.Span> 的內容子系。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## 範例  
 下列範例會建立新的 <xref:System.Windows.Documents.Run> 項目，並將其插入至 <xref:System.Windows.Documents.Span> 的開頭。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## 範例  
 下列範例會取得 <xref:System.Windows.Documents.Span> 中包含的最上層 <xref:System.Windows.Documents.Inline> 項目。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## 範例  
 下列範例會刪除 <xref:System.Windows.Documents.Span> 中的最後一個 <xref:System.Windows.Documents.Inline> 項目。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## 範例  
 下列範例會清除 <xref:System.Windows.Documents.Span> 的所有內容 \(<xref:System.Windows.Documents.Inline> 項目\)。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## 請參閱  
 <xref:System.Windows.Documents.BlockCollection>   
 <xref:System.Windows.Documents.InlineCollection>   
 <xref:System.Windows.Documents.ListItemCollection>   
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [透過 Blocks 屬性管理 FlowDocument ](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [透過 Columns 屬性管理資料表的資料行](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [透過 RowGroups 屬性管理資料表的資料列群組](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)