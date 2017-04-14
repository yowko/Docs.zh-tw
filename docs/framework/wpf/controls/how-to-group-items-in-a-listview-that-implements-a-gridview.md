---
title: "如何：實作 GridView 的 ListView 中的群組項目 | Microsoft Docs"
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
  - "GridView 控制項, 群組項目"
  - "在實作 GridView 的 ListView 中群組項目"
  - "ListView 控制項, 使用 GridViews 群組項目"
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：實作 GridView 的 ListView 中的群組項目
本範例說明如何在 <xref:System.Windows.Controls.ListView> 控制項的 <xref:System.Windows.Controls.GridView> 檢視模式中，顯示群組項目。  
  
## 範例  
 若要在 <xref:System.Windows.Controls.ListView> 中顯示群組項目，請定義 <xref:System.Windows.Data.CollectionViewSource>。  下列範例會顯示 <xref:System.Windows.Data.CollectionViewSource>，它會根據 `Catalog` 資料欄位的值將資料項目分組。  
  
 [!code-xml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 下列範例會將 <xref:System.Windows.Controls.ListView> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 設為前述範例定義的 <xref:System.Windows.Data.CollectionViewSource>。  此範例也會定義實作 <xref:System.Windows.Controls.Expander> 控制項的 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>。  
  
 [!code-xml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)