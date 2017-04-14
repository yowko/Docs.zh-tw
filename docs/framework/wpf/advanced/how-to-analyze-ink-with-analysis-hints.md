---
title: "如何：以分析提示分析筆墨 | Microsoft Docs"
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
  - "AnalysisHintNode 物件"
  - "分析筆墨"
  - "筆墨, AnalysisHintNode 物件"
  - "筆墨, 分析"
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：以分析提示分析筆墨
<xref:System.Windows.Ink.AnalysisHintNode> 會提供附加至 <xref:System.Windows.Ink.InkAnalyzer> 的提示。  提示適用於 <xref:System.Windows.Ink.AnalysisHintNode> 的 <xref:System.Windows.Ink.ContextNode.Location%2A> 屬性所指定的區域，並提供額外的內容給筆墨分析器，以提高辨識精確度。  <xref:System.Windows.Ink.InkAnalyzer> 在分析取自提示區中的筆墨時，會套用這個內容資訊。  
  
## 範例  
 下列範例中的應用程式，以接受筆墨輸入的形式 <xref:System.Windows.Ink.AnalysisHintNode> 使用多個物件。  這個應用程式會使用 <xref:System.Windows.Ink.AnalysisHintNode.Factoid%2A> 屬性，提供表單上每一個輸入的內容資訊。  應用程式會利用背景分析功能來分析筆墨，並在使用者停止新增筆墨後五秒內，清除所有筆墨形式。  
  
 [!code-xml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]