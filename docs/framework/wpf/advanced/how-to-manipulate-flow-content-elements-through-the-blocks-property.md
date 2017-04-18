---
title: "如何：透過 Blocks 屬性管理非固定格式內容項目 | Microsoft Docs"
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
  - "Blocks 屬性, 管理非固定格式內容項目"
  - "文件, 透過 Blocks 屬性管理非固定格式內容項目"
  - "非固定格式內容項目, 透過 Blocks 屬性管理"
  - "屬性, Blocks, 管理非固定格式內容項目"
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：透過 Blocks 屬性管理非固定格式內容項目
這些範例示範可以透過 **Blocks** 屬性對非固定格式內容項目執行的幾項常見作業。  這個屬性用於加入和移除 <xref:System.Windows.Documents.BlockCollection> 的項目。  具有 **Blocks** 屬性的非固定格式內容項目包括：  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 雖然這些範例中都是使用 <xref:System.Windows.Documents.Section> 做為非固定格式內容項目，但這些方法也適用於裝載非固定格式內容項目集合的所有項目。  
  
## 範例  
 下列範例會建立新的 <xref:System.Windows.Documents.Section>，然後使用 **Add** 方法將新 Paragraph 加入至 **Section** 內容。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## 範例  
 下列範例會建立新的 <xref:System.Windows.Documents.Paragraph> 項目，並將其插入至 <xref:System.Windows.Documents.Section> 的開頭。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## 範例  
 下列範例會取得 <xref:System.Windows.Documents.Section> 中包含的最上層 <xref:System.Windows.Documents.Block> 項目。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## 範例  
 下列範例會刪除 <xref:System.Windows.Documents.Section> 中的最後一個 <xref:System.Windows.Documents.Block> 項目。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## 範例  
 下列範例會清除 <xref:System.Windows.Documents.Section> 的所有內容 \(<xref:System.Windows.Documents.Block> 項目\)。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## 請參閱  
 <xref:System.Windows.Documents.BlockCollection>   
 <xref:System.Windows.Documents.InlineCollection>   
 <xref:System.Windows.Documents.ListItemCollection>   
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [透過 RowGroups 屬性管理資料表的資料列群組](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)   
 [透過 Columns 屬性管理資料表的資料行](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [透過 RowGroups 屬性管理資料表的資料列群組](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)