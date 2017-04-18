---
title: "如何：以程式設計的方式將項目插入文字 | Microsoft Docs"
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
  - "項目, 插入至文字"
  - "將項目插入至文字"
  - "文字動畫範例"
  - "文字, 插入項目"
  - "TextPointer 物件"
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：以程式設計的方式將項目插入文字
下列範例顯示如何使用兩個 <xref:System.Windows.Documents.TextPointer> 物件，指定文字內要套用 <xref:System.Windows.Documents.Span> 項目的範圍。  
  
## 範例  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 下圖顯示這個範例的外觀。  
  
 ![已套用至某一文字範圍的 Span 項目](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow\_InsertElementIntoTextProgrammatically")  
  
## 請參閱  
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)