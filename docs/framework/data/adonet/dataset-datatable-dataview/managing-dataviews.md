---
title: 管理 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: c07f521b94f23b479281b0314d6b89a095ee9624
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181240"
---
# <a name="managing-dataviews"></a>管理 DataView

您可以使用 <xref:System.Data.DataViewManager> 管理 <xref:System.Data.DataView> 內所有資料表的檢視設定。 如果您有想要系結至多個資料表的控制項（例如導覽關聯性的方格）， **DataViewManager** 是理想的選擇。  
  
 **DataViewManager**包含物件的集合 <xref:System.Data.DataViewSetting> ，這些物件是用來在中設定資料表的視圖設定 <xref:System.Data.DataSet> 。 <xref:System.Data.DataViewSettingCollection> <xref:System.Data.DataViewSetting> 針對**資料集中**的每個資料表，各包含一個物件。 您可以使用其**DataViewSetting**來設定參考資料表的預設**ApplyDefaultSort**、 **Sort**、 **RowFilter**和**RowStateFilter**屬性。 您可以依名稱或序數參考來參考特定資料表的 **DataViewSetting** ，或是傳遞該特定資料表物件的參考。 您可以使用**DataViewSettings**屬性來存取**DataViewManager**中的**DataViewSetting**物件集合。  
  
 下列程式碼範例會使用 SQL Server **Northwind**資料庫資料表、**客戶**、**訂單**及**訂單詳細資料來**填滿**資料集**、建立資料表之間的關聯性、使用**DataViewManager**來設定預設的**DataView**設定，以及將**DataGrid**系結至**DataViewManager**。 此範例會設定**資料集中**所有資料表的預設**DataView**設定，以依資料表的主鍵排序 (**ApplyDefaultSort**  =  **true**) ，然後將**Customers**資料表的排序次序修改為依**公司名稱**排序。  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [DataView](dataviews.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
