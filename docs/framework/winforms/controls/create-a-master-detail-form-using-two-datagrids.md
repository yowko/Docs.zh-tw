---
title: "如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單 | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
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
  - "DataGridView 控制項 [Windows Form], 主從式表單"
  - "主從式清單, 建立"
  - "父子資料表, 在 Windows Form 上顯示"
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單
下列程式碼範例會使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項繫結至兩個 <xref:System.Windows.Forms.BindingSource> 元件來建立主從式表單。  資料來源是 <xref:System.Data.DataSet>，包含來自 Northwind SQL Server 範例資料庫的 `Customers` 和 `Orders` 資料表，以及透過 `CustomerID` 資料行和這兩者產生關聯的 <xref:System.Data.DataRelation>。  
  
 一個 <xref:System.Windows.Forms.BindingSource> 會繫結至資料集中的父代 `Customers` 資料表。  此資料會顯示在 <xref:System.Windows.Forms.DataGridView> 主控制項。  其他 <xref:System.Windows.Forms.BindingSource> 會繫結至第一個資料連接器。  第二個 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性會設為 <xref:System.Data.DataRelation> 的名稱。  這會導致相關的 <xref:System.Windows.Forms.DataGridView> 詳細資料控制項顯示 `Orders` 子資料表的資料列，對應到 <xref:System.Windows.Forms.DataGridView> 主控制項中的目前資料列。  
  
 如需此程式碼範例的完整說明，請參閱[逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要\/詳細表單](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagrids.md)。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## .NET Framework 安全性  
 在連接字串內儲存敏感性資訊，例如密碼，會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要\/詳細表單](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagrids.md)   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)