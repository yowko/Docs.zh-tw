---
title: "如何：調整段落之間的間距 | Microsoft Docs"
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
  - "文件, 調整段落之間的間距"
  - "段落, 間距"
  - "段落之間的間距"
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：調整段落之間的間距
這個範例顯示如何調整或消除非固定格式內容中各段落間的間距。  
  
 在非固定格式內容中，段落間所出現的多餘間格是由這些段落上所設定的邊界所致，因此，段落間的間距可藉由調整這些段落的邊界來控制。  若要完全消除兩個段落間的多餘間距，請將段落的邊界設為 **0**。  若要讓整個 <xref:System.Windows.Documents.FlowDocument> 的段落間皆使用統一的間距，請使用樣式對 <xref:System.Windows.Documents.FlowDocument> 中所有的段落設定統一的邊界值。  
  
 請務必留意，兩個相鄰段落的邊界會「縮疊」為兩個邊界中的較大者，而非變成兩倍大。  因此，如果兩個相鄰段落的邊界分別為 20 個像素與 40 個像素，段落間所產生的間距即為兩個邊界值中的較大者，也就是 40 個像素。  
  
## 範例  
 下列範例會使用樣式設定，將 <xref:System.Windows.Documents.FlowDocument> 中所有 <xref:System.Windows.Documents.Paragraph> 項目的邊界設為 **0**，這個值可以有效消除 <xref:System.Windows.Documents.FlowDocument> 中各段落間的多餘間距。  
  
 [!code-xml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]