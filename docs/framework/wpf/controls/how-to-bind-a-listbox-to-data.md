---
title: "如何：將 ListBox 繫結至資料 | Microsoft Docs"
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
  - "資料繫結, 至 ListBox 控制項"
  - "資料繫結, ListBox 控制項"
  - "ListBox 控制項, 將資料繫結至"
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：將 ListBox 繫結至資料
應用程式開發人員可以建立 <xref:System.Windows.Controls.ListBox> 控制項，而不需要個別指定每個 <xref:System.Windows.Controls.ListBoxItem> 的內容。  您可以使用資料繫結 \(Data Binding\)，將資料繫結至個別項目。  
  
 下列範例顯示如何透過將資料繫結至資料來源 *Colors*，以建立填入 \(Populate\) <xref:System.Windows.Controls.ListBoxItem> 項目的 <xref:System.Windows.Controls.ListBox>。  在這個案例中，並不需要使用 <xref:System.Windows.Controls.ListBoxItem> 標記指定每個項目的內容。  
  
## 範例  
 [!code-xml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.Controls.ListBoxItem>   
 [控制項](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)