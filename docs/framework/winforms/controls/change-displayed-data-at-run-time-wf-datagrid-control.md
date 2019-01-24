---
title: HOW TO：在 Windows Forms DataGrid 控制項中的執行階段變更顯示的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: fc0fe47d728a196de81f7bf099e3a25ac2bb9211
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605561"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>HOW TO：在 Windows Forms DataGrid 控制項中的執行階段變更顯示的資料
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 建立 Windows Form 後<xref:System.Windows.Forms.DataGrid>使用的設計階段功能，您可能也想要以動態方式變更的項目<xref:System.Data.DataSet>za běhu 方格的物件。 這可能包括資料表的個別值的變更，或變更資料來源繫結至<xref:System.Windows.Forms.DataGrid>控制項。 個別的值變更會透過<xref:System.Data.DataSet>物件，不<xref:System.Windows.Forms.DataGrid>控制項。  
  
### <a name="to-change-data-programmatically"></a>若要以程式設計方式變更資料  
  
1.  指定所需的資料表，從<xref:System.Data.DataSet>物件及所需資料列和資料表中的欄位，以及設定儲存格等於新值。  
  
    > [!NOTE]
    >  若要指定的第一個資料表<xref:System.Data.DataSet>或第一列的資料表，請使用 0。  
  
     下列範例示範如何變更資料集的第一個資料表的第一列的第二個項目，依序按一下`Button1`。 <xref:System.Data.DataSet> (`ds`) 和資料表 (`0`和`1`) 先前所建立。  
  
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
  
     在執行的階段，您可以使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法來繫結<xref:System.Windows.Forms.DataGrid>不同的資料來源的控制項。 例如，您可能會有數個[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]資料控制項，每個都連接到不同的資料庫。  
  
### <a name="to-change-the-datasource-programmatically"></a>若要以程式設計方式變更資料來源  
  
1.  設定<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法的資料來源和您想要繫結至資料表的名稱。  
  
     下列範例示範如何變更的日期來源 using<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法，以[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]連線至 Pubs 資料庫中 Authors 資料表的資料控制項 (adoPubsAuthors)。  
  
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
- [ADO.NET 資料集](../../../../docs/framework/data/adonet/ado-net-datasets.md)
- [如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [如何：將資料表和資料行新增至 Windows Forms DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [如何：將 Windows Forms DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
