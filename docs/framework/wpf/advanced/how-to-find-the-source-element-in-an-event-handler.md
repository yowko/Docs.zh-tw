---
title: "如何：尋找事件處理常式中的來源項目 | Microsoft Docs"
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
  - "事件處理常式, 尋找來源項目"
  - "事件處理常式中的來源項目"
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：尋找事件處理常式中的來源項目
本範例示範如何尋找事件處理常式 \(Event Handler\) 中的來源項目。  
  
## 範例  
 下列範例顯示在程式碼後置 \(Code\-Behind\) 檔案中宣告的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式。  當使用者按一下附加此處理常式的按鈕時，處理常式就會變更屬性值。  處理常式程式碼會使用事件引數中回報之路由事件資料的 <xref:System.Windows.RoutedEventArgs.Source%2A> 屬性，變更 <xref:System.Windows.RoutedEventArgs.Source%2A> 項目上的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性。  
  
 [!code-xml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## 請參閱  
 <xref:System.Windows.RoutedEventArgs>   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)