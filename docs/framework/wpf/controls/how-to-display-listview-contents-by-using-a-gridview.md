---
title: "如何：使用 GridView 顯示 ListView 內容 | Microsoft Docs"
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
  - "GridView, 顯示 ListView 內容"
  - "ListView 控制項, 使用 GridView 顯示"
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用 GridView 顯示 ListView 內容
本範列示範如何定義 <xref:System.Windows.Controls.ListView> 控制項的 <xref:System.Windows.Controls.GridView> 檢視模式。  
  
## 範例  
 您可以透過指定 <xref:System.Windows.Controls.GridViewColumn> 物件來定義 <xref:System.Windows.Controls.GridView> 的檢視模式。  下列範例示範如何定義 <xref:System.Windows.Controls.GridViewColumn> 物件，這些物件是繫結到為 <xref:System.Windows.Controls.ListView> 控制項指定的資料內容。  這個 <xref:System.Windows.Controls.GridView> 範例指定三個 <xref:System.Windows.Controls.GridViewColumn> 物件，分別對應至 `EmployeeInfoDataSource` \(已設定為 <xref:System.Windows.Controls.ListView> 控制項的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>\) 的 `FirstName`、`LastName` 和 `EmployeeNumber` 欄位。  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示這個範例的外觀。  
  
 ![ListView 與 GridView 輸出](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
## 請參閱  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)