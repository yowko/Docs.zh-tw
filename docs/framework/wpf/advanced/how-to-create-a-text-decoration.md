---
title: "如何：建立文字裝飾 | Microsoft Docs"
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
  - "基準類型"
  - "字型, 基準"
  - "字型, 頂線"
  - "字型, 刪除線"
  - "字型, 底線"
  - "頂線類型"
  - "刪除線類型"
  - "文字, 裝飾"
  - "印刷樣式, 文字裝飾"
  - "底線類型"
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立文字裝飾
<xref:System.Windows.TextDecoration> 物件是可以加入文字的視覺裝飾。  文字裝飾有四種：底線、基準線、刪除線和頂線。  下列範例顯示文字裝飾與文字的相對位置。  
  
 ![文字裝飾位置的圖表](../../../../docs/framework/wpf/advanced/media/textdecoration01.png "TextDecoration01")  
文字裝飾類型的範例  
  
 若要為文字加入文字裝飾，請建立 <xref:System.Windows.TextDecoration> 物件並修改其屬性。  使用 <xref:System.Windows.TextDecoration.Location%2A> 屬性可指定文字裝飾的顯示位置，如底線。  使用 <xref:System.Windows.TextDecoration.Pen%2A> 屬性可指定文字裝飾的外觀，如純色填色或漸層色彩。  若未指定 <xref:System.Windows.TextDecoration.Pen%2A> 屬性的值，裝飾即會預設為與文字相同的色彩。  定義 <xref:System.Windows.TextDecoration> 物件後，將其加入至所需文字物件的 <xref:System.Windows.TextDecorations> 集合中。  
  
 下列範例顯示利用線形漸層筆刷和虛線畫筆加上樣式的文字裝飾。  
  
 ![具有線性漸層底線的文字裝飾](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
利用線形漸層筆刷和虛線畫筆加上底線樣式的範例  
  
 <xref:System.Windows.Documents.Hyperlink> 物件是內嵌層級非固定格式內容項目，這個項目可讓您在非固定格式內容中裝載 \(Host\) 超連結 \(Hyperlink\)。  根據預設，<xref:System.Windows.Documents.Hyperlink> 會使用 <xref:System.Windows.TextDecoration> 物件顯示底線。  <xref:System.Windows.TextDecoration> 物件可將最佳效能具現化，特別是在您擁有多個 <xref:System.Windows.Documents.Hyperlink> 物件時。  如果大量使用 <xref:System.Windows.Documents.Hyperlink> 項目，您可以考慮只有在觸發事件 \(如 <xref:System.Windows.ContentElement.MouseEnter> 事件\) 時才顯示底線。  
  
 在下列範例中，"My MSN" 連結的底線是動態的，只有在 <xref:System.Windows.ContentElement.MouseEnter> 事件觸發時才會出現。  
  
 ![顯示 TextDecoration 的超連結](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
使用 TextDecorations 定義的超連結  
  
 如需詳細資訊，請參閱 [指定超連結是否要加上底線](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)。  
  
## 範例  
 下列程式碼範例中的底線文字裝飾使用預設字型值。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 在下列程式碼範例中，會使用畫筆的實心彩色筆刷建立底線文字裝飾。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 在下列程式碼範例中，會使用虛線畫筆的線形漸層筆刷建立底線文字裝飾。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## 請參閱  
 <xref:System.Windows.TextDecoration>   
 <xref:System.Windows.Documents.Hyperlink>   
 [指定超連結是否要加上底線](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)