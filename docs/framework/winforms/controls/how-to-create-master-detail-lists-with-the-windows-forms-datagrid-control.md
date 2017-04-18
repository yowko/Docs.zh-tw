---
title: "如何：使用 Windows Form DataGrid 控制項建立主從式清單 | Microsoft Docs"
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
  - "DataGrid 控制項 [Windows Form], 主從式清單"
  - "主從式清單"
  - "關聯資料表, 在 DataGrid 控制項中顯示"
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 Windows Form DataGrid 控制項建立主從式清單
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 如果您的 <xref:System.Data.DataSet> 包含一系列關聯的資料表，您可以使用兩個 <xref:System.Windows.Forms.DataGrid> 控制項，以主從式的格式顯示資料。  一個 <xref:System.Windows.Forms.DataGrid> 指定為主版資料格，第二個則指定為詳細資料資料格。  當您在主要清單中選取項目時，相關的所有子項目都將顯示在詳細資料清單中。  例如，如果 <xref:System.Data.DataSet> 包含 Customers 資料表和關聯的 Orders 資料表，則您會將 Customers 資料表指定為主版資料格，並將 Orders 資料表指定為詳細資料資料格。  在主要資料格中選取客戶時，Orders 資料表中與該客戶相關的所有訂單都會顯示於詳細資料格中。  
  
### 若要以程式設計方式設定主從式關聯性  
  
1.  建立兩個新的 <xref:System.Windows.Forms.DataGrid> 控制項並設定它們的屬性。  
  
2.  將資料表加入至資料集。  
  
3.  宣告 <xref:System.Data.DataRelation> 型別的變數，代表要建立的關聯。  
  
4.  以指定關聯性名稱以及指定資料表、資料行和繫結兩個資料表的項目來產生關聯性。  
  
5.  將關聯性加入至 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Relations%2A> 集合。  
  
6.  使用 <xref:System.Windows.Forms.DataGrid> 的 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，將每個資料格繫結至 <xref:System.Data.DataSet>。  
  
     下列範例會示範如何在先前產生的 <xref:System.Data.DataSet> \(`ds`\) 中，設定 Customers 和 Orders 資料表之間的主從式關聯性。  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## 請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [如何：將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)