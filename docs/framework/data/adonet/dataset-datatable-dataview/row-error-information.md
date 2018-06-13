---
title: 資料列錯誤資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 6f3f332d4b9bd0be9934c7bf7722e8ff71c4eb2f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767189"
---
# <a name="row-error-information"></a><span data-ttu-id="b4d97-102">資料列錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="b4d97-102">Row Error Information</span></span>
<span data-ttu-id="b4d97-103">編輯 <xref:System.Data.DataTable> 中的值時，若要避免必須在每次發生資料列錯誤時都回應，則可以將錯誤資訊加入至資料列中，供日後使用。</span><span class="sxs-lookup"><span data-stu-id="b4d97-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="b4d97-104">針對這項用途，<xref:System.Data.DataRow> 物件會為每個資料列提供 <xref:System.Data.DataRow.RowError%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b4d97-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="b4d97-105">將資料加入至**RowError**屬性**DataRow**設定<xref:System.Data.DataRow.HasErrors%2A>屬性**DataRow**至**true**。</span><span class="sxs-lookup"><span data-stu-id="b4d97-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="b4d97-106">如果**DataRow**屬於**DataTable**，和**DataRow.HasErrors**是**true**、 **DataTable.HasErrors**屬性也是**true**。</span><span class="sxs-lookup"><span data-stu-id="b4d97-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="b4d97-107">這同樣適用於**資料集**的**DataTable**所屬。</span><span class="sxs-lookup"><span data-stu-id="b4d97-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="b4d97-108">在測試是否有錯誤時，您可以檢查**HasErrors**屬性來判斷錯誤資訊是否已新增的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="b4d97-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="b4d97-109">如果**HasErrors**是**true**，您可以使用<xref:System.Data.DataTable.GetErrors%2A>方法**DataTable**傳回，並檢查的錯誤，資料列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b4d97-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4d97-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4d97-110">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="b4d97-111">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="b4d97-111">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="b4d97-112">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b4d97-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
