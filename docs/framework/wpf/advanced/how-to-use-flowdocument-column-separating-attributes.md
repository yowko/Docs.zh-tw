---
title: "如何：使用 FlowDocument 資料行分隔屬性 | Microsoft Docs"
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
  - "資料行分隔屬性"
  - "文件, FlowDocument 資料行分隔屬性"
  - "FlowDocument 資料行分隔屬性"
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用 FlowDocument 資料行分隔屬性
此範例顯示如何使用 <xref:System.Windows.Documents.FlowDocument> 的資料行分隔功能。  
  
## 範例  
 下列範例將定義 <xref:System.Windows.Documents.FlowDocument>，並設定 <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、<xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A> 與 <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> 屬性。  <xref:System.Windows.Documents.FlowDocument> 包含範例內容的單一段落。  
  
 [!code-xml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 下圖顯示所呈現之 <xref:System.Windows.Documents.FlowDocument> 中的 <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、<xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A> 與 <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> 屬性的效果。  
  
 ![螢幕擷取畫面: FlowDocument 的內部資料行](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")