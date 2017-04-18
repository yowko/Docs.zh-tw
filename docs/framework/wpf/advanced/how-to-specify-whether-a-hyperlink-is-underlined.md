---
title: "如何：指定超連結是否要加上底線 | Microsoft Docs"
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
  - "類別, TextDecoration"
  - "Hyperlink 控制項類型"
  - "TextDecoration 類別"
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：指定超連結是否要加上底線
<xref:System.Windows.Documents.Hyperlink> 物件是內嵌層級非固定格式內容項目，這個項目可讓您在非固定格式內容中裝載 \(Host\) 超連結 \(Hyperlink\)。  根據預設，<xref:System.Windows.Documents.Hyperlink> 會使用 <xref:System.Windows.TextDecoration> 物件顯示底線。  <xref:System.Windows.TextDecoration> 物件可將最佳效能具現化，特別是在您擁有多個 <xref:System.Windows.Documents.Hyperlink> 物件時。  如果大量使用 <xref:System.Windows.Documents.Hyperlink> 項目，您可以考慮只有在觸發事件 \(如 <xref:System.Windows.ContentElement.MouseEnter> 事件\) 時才顯示底線。  
  
 在下列範例中，"My MSN" 連結的底線是動態的，只有在 <xref:System.Windows.ContentElement.MouseEnter> 事件觸發時才會出現。  
  
 ![顯示 TextDecoration 的超連結](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
使用 TextDecorations 定義的超連結  
  
## 範例  
 下列標記範例顯示定義為有底線及没有底線的 <xref:System.Windows.Documents.Hyperlink>：  
  
 [!code-xml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 下列程式碼範例示範如何在 <xref:System.Windows.ContentElement.MouseEnter> 事件上建立 <xref:System.Windows.Documents.Hyperlink> 的底線，並在 <xref:System.Windows.ContentElement.MouseLeave> 事件上將它移除。  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## 請參閱  
 <xref:System.Windows.TextDecoration>   
 <xref:System.Windows.Documents.Hyperlink>   
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [建立文字裝飾](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)