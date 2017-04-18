---
title: "如何：依名稱尋找項目 | Microsoft Docs"
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
  - "項目, 依名稱尋找"
  - "FindName 方法"
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：依名稱尋找項目
本範例描述如何依據 <xref:System.Windows.FrameworkElement.Name%2A> 值使用 <xref:System.Windows.FrameworkElement.FindName%2A> 方法找出項目。  
  
## 範例  
 在此範例中，依照名稱尋找特定項目的方法會撰寫為按鈕的事件處理常式。  `stackPanel` 是要搜尋的根 <xref:System.Windows.FrameworkElement> 的 <xref:System.Windows.FrameworkElement.Name%2A>，接著範例方法會以視覺化的方式指出，透過轉型為 <xref:System.Windows.Controls.TextBlock> 並且變更其中一個 <xref:System.Windows.Controls.TextBlock> 可見 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 屬性的方式找到的項目。  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]