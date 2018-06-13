---
title: 複製資料集內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: bee91a6406fd48894580ce6223a5682dbadab380
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757290"
---
# <a name="copying-dataset-contents"></a>複製資料集內容
您可以建立一份<xref:System.Data.DataSet>，讓您可以使用資料，而不會影響原始資料，或處理的資料子集**資料集**。 當複製**資料集**，您可以：  
  
-   建立完全相同複本**資料集**，包括結構描述、 資料、 資料列狀態資訊，以及資料列版本。  
  
-   建立**資料集**，其中包含針對現有的結構描述**資料集**，但已修改的資料列。 您可以傳回已修改的所有資料列，或指定特定**Getchanges**。 如需資料列狀態的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
-   複製結構描述或關聯式結構**資料集**，而不複製任何資料列。 使用 <xref:System.Data.DataTable>，可以將資料列匯入現有的 <xref:System.Data.DataTable.ImportRow%2A>。  
  
 若要建立的完全相同複本**資料集**包含結構描述和資料，請使用<xref:System.Data.DataSet.Copy%2A>方法**資料集**。 下列程式碼範例示範如何建立完全相同的複本**資料集**。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 若要建立一份**資料集**包含結構描述和只有資料表示的**Added**， **Modified**，或**刪除**資料列，使用<xref:System.Data.DataSet.GetChanges%2A>方法**資料集**。 您也可以使用**Datarowstate**藉由傳遞傳回具有指定的資料列狀態的資料列**Getchanges**時呼叫的值**Datarowstate**。 下列程式碼範例示範如何傳遞**Getchanges**呼叫時**Datarowstate**。  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 若要建立一份**資料集**只包含結構描述，請使用<xref:System.Data.DataSet.Clone%2A>方法**資料集**。 您也可以將現有的資料列加入複製**資料集**使用**ImportRow**方法**DataTable**。 **ImportRow**將資料、 資料列狀態和資料列版本資訊加入至指定的資料表。 資料行值只會被加入資料行名稱相符且資料型別相容之處。  
  
 下列程式碼範例會建立複製的**資料集**然後將原始資料列**資料集**至**客戶**資料表中**資料集**客戶複製其中**CountryRegion**資料行有值為"Germany"。  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
