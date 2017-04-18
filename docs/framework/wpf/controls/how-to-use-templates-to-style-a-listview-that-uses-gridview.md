---
title: "如何：使用範本為使用 GridView 的 ListView 設定樣式 | Microsoft Docs"
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
  - "ListView 控制項, 樣式"
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用範本為使用 GridView 的 ListView 設定樣式
本範例說明如何使用 <xref:System.Windows.DataTemplate> 和 <xref:System.Windows.Style> 物件，指定使用 <xref:System.Windows.Controls.GridView> 檢視模式之 <xref:System.Windows.Controls.ListView> 控制項的外觀。  
  
## 範例  
 下列範例顯示 <xref:System.Windows.Style> 和 <xref:System.Windows.DataTemplate> 物件如何自訂 <xref:System.Windows.Controls.GridViewColumn> 的資料行行首外觀。  
  
 [!code-xml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 下列範例顯示如何使用 <xref:System.Windows.Style> 和 <xref:System.Windows.DataTemplate> 物件設定 <xref:System.Windows.Controls.GridViewColumn> 的 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> 和 <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> 屬性。  <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 屬性會定義資料行儲存格的內容。  
  
 [!code-xml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 您只能使用 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> 和 <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> 這兩個屬性來自訂 <xref:System.Windows.Controls.GridView> 控制項的資料行行首外觀。  如需詳細資訊，請參閱 [GridView 資料行行首樣式和範本概觀](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)。  
  
 下列範例顯示如何定義 <xref:System.Windows.DataTemplate>，以用來自訂 <xref:System.Windows.Controls.GridViewColumn> 中的資料格外觀。  
  
 [!code-xml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 下列範例顯示如何使用這個 <xref:System.Windows.DataTemplate> 定義 <xref:System.Windows.Controls.GridViewColumn> 儲存格的內容。  此樣板用來取代前面 <xref:System.Windows.Controls.GridViewColumn> 範例的 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 屬性。  
  
 [!code-xml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)