---
title: "如何：使用含階層式 XML 資料的主從式模式 | Microsoft Docs"
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
  - "資料繫結, 主從式資料開發架構"
  - "主從式資料開發架構"
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用含階層式 XML 資料的主從式模式
這個範例顯示如何使用 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料實作主從式案例。  
  
## 範例  
 這個範例是 [使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)中討論之範例的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料版本。  在這個範例中，資料是來自檔案 `League.xml`。  請注意第三個 <xref:System.Windows.Controls.ListBox> 控制項如何以繫結至 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性的方式追蹤第二個 <xref:System.Windows.Controls.ListBox> 控制項中的選取範圍變更。  
  
 [!code-xml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## 請參閱  
 <xref:System.Windows.HierarchicalDataTemplate>   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)