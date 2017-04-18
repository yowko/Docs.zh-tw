---
title: "如何：變更 ListView 中資料行的水平對齊 | Microsoft Docs"
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
  - "ListView 控制項, 水平對齊"
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：變更 ListView 中資料行的水平對齊
根據預設，<xref:System.Windows.Controls.ListViewItem> 中每個資料行的內容都是靠左對齊。  您可以藉由提供 <xref:System.Windows.DataTemplate> 並在 <xref:System.Windows.DataTemplate> 內的項目上設定 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性，以變更每個資料行的對齊方式。  本主題示範 <xref:System.Windows.Controls.ListView> 如何依預設對齊內容，以及如何變更 <xref:System.Windows.Controls.ListView> 其中一個資料行的對齊方式。  
  
## 範例  
 在下列範例中，`Title` 和 `ISBN` 資料行中的資料是靠左對齊。  
  
 [!code-xml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 若要變更 `ISBN` 資料行的對齊方式，您需要指定每個 <xref:System.Windows.Controls.ListViewItem> 的 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 屬性為 <xref:System.Windows.HorizontalAlignment>，讓每個 <xref:System.Windows.Controls.ListViewItem> 中的項目可以擴展或沿著每個資料行的整個寬度放置。  由於 <xref:System.Windows.Controls.ListView> 繫結至資料來源，您必須建立設定 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 的樣式。  接著，您需要使用 <xref:System.Windows.DataTemplate> 來顯示內容，而不是使用 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 屬性。  若要顯示每個範本的 `ISBN`，<xref:System.Windows.DataTemplate> 只要包含將 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性設定為 <xref:System.Windows.HorizontalAlignment> 的 <xref:System.Windows.Controls.TextBlock> 即可。  
  
 下列範例定義將 `ISBN` 設為靠右對齊所需的樣式和 <xref:System.Windows.DataTemplate>，並變更 <xref:System.Windows.Controls.GridViewColumn> 來參考 <xref:System.Windows.DataTemplate>。  
  
 [!code-xml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)