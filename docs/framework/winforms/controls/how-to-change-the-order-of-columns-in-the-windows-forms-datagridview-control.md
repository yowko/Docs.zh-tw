---
title: "如何：變更 Windows Form DataGridView 控制項資料行的順序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料行 [Windows Form], 變更順序"
  - "資料格, 變更資料行順序"
  - "DataGridView 控制項 [Windows Form], 資料行順序"
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：變更 Windows Form DataGridView 控制項資料行的順序
當您使用 <xref:System.Windows.Forms.DataGridView> 顯示來自資料來源的資料時，資料來源結構描述中的資料行有時不會以您想要的順序顯示。  您可以使用 <xref:System.Windows.Forms.DataGridViewColumn> 類別的 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> 屬性來變更資料行的顯示順序。  
  
 下列程式碼範例會重新調整繫結至 Northwind 範例資料庫中的 Customers 資料表時，所自動產生之一些資料行的位置。  如需如何將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至資料庫資料表的詳細資訊，請參閱[如何：將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[如何：使用設計工具變更 Windows Form DataGridView 控制項中資料行的順序](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項，這個控制項會繫結至具有指定資料行名稱的資料表，例如 Northwind 範例資料庫中的 `Customers` 資料表。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName>、<xref:System.Data?displayProperty=fullName> 和 <xref:System.Xml?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [如何：將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)