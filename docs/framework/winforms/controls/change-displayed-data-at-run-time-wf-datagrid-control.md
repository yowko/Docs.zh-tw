---
title: "如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料 | Microsoft Docs"
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
  - "儲存格, 變更 DataGrid 儲存格值"
  - "DataGrid 控制項 [Windows Form], 資料繫結"
  - "DataGrid 控制項 [Windows Form], 在執行階段動態變更"
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 當您使用設計階段功能建立了 Windows Form <xref:System.Windows.Forms.DataGrid> 後，可能也會希望在執行階段時動態變更資料格 <xref:System.Data.DataSet> 物件的項目。  這可能包含變更資料表的個別值，或變更繫結至 <xref:System.Windows.Forms.DataGrid> 控制項的資料來源。  個別值的變更是透過 <xref:System.Data.DataSet> 物件達成，而不是 <xref:System.Windows.Forms.DataGrid> 控制項。  
  
### 若要以程式設計的方式變更資料  
  
1.  指定 <xref:System.Data.DataSet> 物件中要變更的資料表和資料表中要變更的資料列和欄位，並將儲存格設定為新的值。  
  
    > [!NOTE]
    >  若要指定 <xref:System.Data.DataSet> 的第一個資料表或資料表的第一個資料列，請使用 0。  
  
     下列範例顯示如何按一下 `Button1` 來變更資料集中第一個資料表的第一個資料列的第二個項目。  <xref:System.Data.DataSet> \(`ds`\) 和資料表 \(`0` 和`1`\) 已預先建立。  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     在執行階段時，您可以使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法將 <xref:System.Windows.Forms.DataGrid> 控制項繫結至不同的資料來源。  例如，您可能有數個 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 資料控制項，而且分別連接至不同的資料庫。  
  
### 若要以程式設計的方式變更 DataSource  
  
1.  將 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法設定為您要繫結至的資料來源和資料表名稱。  
  
     下列範例顯示如何使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法將資料來源變更為連接至 Pubs 資料庫中 Authors 資料表的 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 資料控制項 \(adoPubsAuthors\)。  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## 請參閱  
 [ADO.NET DataSet](../../../../docs/framework/data/adonet/ado-net-datasets.md)   
 [如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [如何：將資料表和資料行加入至 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [如何：將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)