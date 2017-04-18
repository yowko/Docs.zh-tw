---
title: "如何：處理 ListView 中每個項目的 MouseDoubleClick 事件 | Microsoft Docs"
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
  - "ListView 控制項, MouseDoubleClick 事件"
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：處理 ListView 中每個項目的 MouseDoubleClick 事件
若要處理 <xref:System.Windows.Controls.ListView> 中項目的事件，您需要在每個 <xref:System.Windows.Controls.ListViewItem> 加入事件處理常式。  當 <xref:System.Windows.Controls.ListView> 繫結至資料來源時，您不會明確建立 <xref:System.Windows.Controls.ListViewItem>，但可以藉由加入 <xref:System.Windows.EventSetter> 至 <xref:System.Windows.Controls.ListViewItem> 的樣式，以處理每個項目的事件。  
  
## 範例  
 下列範例會建立資料繫結 <xref:System.Windows.Controls.ListView> 並建立 <xref:System.Windows.Style>，以將事件處理常式加入到每個 <xref:System.Windows.Controls.ListViewItem>。  
  
 [!code-xml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 下列範例會處理 <xref:System.Windows.Controls.Control.MouseDoubleClick> 事件。  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  雖然將 <xref:System.Windows.Controls.ListView> 繫結至資料來源是最常見的做法，不過您可以使用樣式，將事件處理常式加入到非資料繫結的 <xref:System.Windows.Controls.ListView> 中的每個 <xref:System.Windows.Controls.ListViewItem>，不論是否明確建立了 <xref:System.Windows.Controls.ListViewItem>。  如需以明確和隱含方式建立 <xref:System.Windows.Controls.ListViewItem> 控制項的詳細資訊，請參閱 <xref:System.Windows.Controls.ItemsControl>。  
  
## 請參閱  
 <xref:System.Xml.XmlElement>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)