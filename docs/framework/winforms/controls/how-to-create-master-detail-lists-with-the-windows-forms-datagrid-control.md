---
title: HOW TO：使用 Windows Forms DataGrid 控制項建立主版詳細資料清單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914756"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>作法：使用 Windows Forms DataGrid 控制項建立主從式清單
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 如果您<xref:System.Data.DataSet>包含一系列相關的資料表, 您可以使用兩<xref:System.Windows.Forms.DataGrid>個控制項, 以主要/詳細資料格式顯示資料。 其中<xref:System.Windows.Forms.DataGrid>一個會被指定為主要方格, 而第二個則指定為詳細資料方格。 當您選取 [主要] 清單中的專案時, [詳細資料] 清單中會顯示所有相關的子專案。 例如, 如果您<xref:System.Data.DataSet>的包含 customers 資料表和相關的 Orders 資料表, 您會將 customers 資料表指定為主要方格, 而 orders 資料表則是詳細資料方格。 從主要方格中選取客戶時, [訂單] 資料表中與該客戶相關聯的所有訂單都會顯示在 [詳細資料] 方格中。  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>以程式設計方式設定主要/詳細資料關聯性  
  
1. 建立兩個<xref:System.Windows.Forms.DataGrid>新的控制項, 並設定其屬性。  
  
2. 將資料表加入至資料集。  
  
3. 宣告類型<xref:System.Data.DataRelation>的變數, 以代表您想要建立的關聯性。  
  
4. 指定關聯性的名稱, 並指定將結合兩個數據表的資料表、資料行和專案, 以具現化關聯性。  
  
5. 將關聯性新增至<xref:System.Data.DataSet>物件的<xref:System.Data.DataSet.Relations%2A>集合。  
  
6. 使用的<xref:System.Windows.Forms.DataGrid> <xref:System.Data.DataSet>方法, 將每個格線系結至。 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>  
  
     下列範例示範如何在先前產生<xref:System.Data.DataSet>的 (`ds`) 中設定 Customers 和 Orders 資料表之間的主要/詳細關係。  
  
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
  
## <a name="see-also"></a>另請參閱

- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將 Windows Forms DataGrid 控制項系結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
