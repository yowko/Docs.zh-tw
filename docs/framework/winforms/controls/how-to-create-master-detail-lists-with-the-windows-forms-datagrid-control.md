---
title: 如何： 使用 Windows Form DataGrid 控制項建立主從式清單
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
ms.openlocfilehash: 528d07b766987bdeca22ce480c601a2bdd324c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>如何：使用 Windows Form DataGrid 控制項建立主從式清單
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 如果您<xref:System.Data.DataSet>包含一系列相關的資料表，您可以使用兩個<xref:System.Windows.Forms.DataGrid>控制項以顯示資料的主要/詳細資料格式。 一個<xref:System.Windows.Forms.DataGrid>指定為主要方格中，與第二個指定為詳細資料方格。 當您的主機清單中選取一個項目時，所有相關的子系項目會顯示在詳細資料清單。 例如，如果您<xref:System.Data.DataSet>包含 Customers 資料表和相關的 Orders 資料表，您會指定為主要的方格的 [客戶] 資料表和訂單資料表詳細資料方格。 從主版方格選取客戶時，所有相關 [Orders] 資料表中與該客戶的訂單會顯示詳細資料方格中。  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>以程式設計方式設定的主要/詳細資料關聯性  
  
1.  建立兩個新<xref:System.Windows.Forms.DataGrid>控制，並設定其屬性。  
  
2.  將資料表加入至資料集。  
  
3.  宣告類型的變數<xref:System.Data.DataRelation>來代表您想要建立的關聯性。  
  
4.  所指定關聯性的名稱，並指定資料表、 資料行和會結合兩個資料表的項目產生關聯性。  
  
5.  加入至關聯性<xref:System.Data.DataSet>物件的<xref:System.Data.DataSet.Relations%2A>集合。  
  
6.  使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法<xref:System.Windows.Forms.DataGrid>繫結至方格的每個<xref:System.Data.DataSet>。  
  
     下列範例示範如何設定主要/詳細資料之間的關聯性中先前產生的客戶和訂單資料表<xref:System.Data.DataSet>(`ds`)。  
  
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
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [操作說明：將 Windows Forms DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
