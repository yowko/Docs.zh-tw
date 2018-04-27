---
title: 如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ea90c3532203a61beded5eceeee5cf535a74b87b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 建立 Windows Form 之後<xref:System.Windows.Forms.DataGrid>使用設計階段功能，您可能也想要以動態方式變更項目的<xref:System.Data.DataSet>在執行階段方格的物件。 這可包括對資料表的個別值或變更資料來源繫結至<xref:System.Windows.Forms.DataGrid>控制項。 個別值的變更會透過<xref:System.Data.DataSet>物件，不<xref:System.Windows.Forms.DataGrid>控制項。  
  
### <a name="to-change-data-programmatically"></a>若要以程式設計方式變更資料  
  
1.  指定所需的資料表，從<xref:System.Data.DataSet>物件和想要的資料列和欄位從資料表和資料格設定為等於新值。  
  
    > [!NOTE]
    >  若要指定的第一個資料表<xref:System.Data.DataSet>或資料表，第一個資料列，請使用 0。  
  
     下列範例示範如何變更資料集的第一個資料表的第一個資料列的第二個項目，依序按一下`Button1`。 <xref:System.Data.DataSet> (`ds`) 和資料表 (`0`和`1`) 先前所建立。  
  
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
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     在執行的階段，您可以使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>繫結方法<xref:System.Windows.Forms.DataGrid>不同的資料來源的控制項。 例如，您可以有數個[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]資料控制項，每個已連線到不同的資料庫。  
  
### <a name="to-change-the-datasource-programmatically"></a>若要以程式設計方式變更資料來源  
  
1.  設定<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法的資料來源和您想要繫結至資料表的名稱。  
  
     下列範例示範如何變更日期來源使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]連線到 Authors 資料表 Pubs 資料庫中的資料控制項 (adoPubsAuthors)。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET 資料集](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [操作說明：將資料表和資料行新增至 Windows Forms DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [操作說明：將 Windows Forms DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
