---
title: "如何：使用 GridViewRowPresenter 顯示資料 | Microsoft Docs"
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
  - "使用 GridViewRowPresenter 顯示資料"
  - "GridViewRowPresenter"
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用 GridViewRowPresenter 顯示資料
本範例說明如何使用 <xref:System.Windows.Controls.GridViewRowPresenter> 和 <xref:System.Windows.Controls.GridViewHeaderRowPresenter> 物件，以顯示資料行中的資料。  
  
## 範例  
 下列範例說明如何使用 <xref:System.Windows.Controls.GridViewRowPresenter> 和 <xref:System.Windows.Controls.GridViewHeaderRowPresenter> 物件以指定 <xref:System.Windows.Controls.GridViewColumnCollection>，以顯示 <xref:System.DateTime> 物件的 <xref:System.DateTime.DayOfWeek%2A> 和 <xref:System.DateTime.Year%2A>。  本範例也為 <xref:System.Windows.Controls.GridViewColumn> 的 <xref:System.Windows.Controls.GridViewColumn.Header%2A> 定義一個 <xref:System.Windows.Style>。  
  
 [!code-xml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## 請參閱  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>   
 <xref:System.Windows.Controls.GridViewRowPresenter>   
 <xref:System.Windows.Controls.GridViewColumnCollection>   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)