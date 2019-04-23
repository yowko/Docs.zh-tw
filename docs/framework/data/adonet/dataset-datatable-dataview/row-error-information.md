---
title: 資料列錯誤資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 89889c5543e6518046bb59b59646ecba715f5e03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152720"
---
# <a name="row-error-information"></a><span data-ttu-id="53bcd-102">資料列錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="53bcd-102">Row Error Information</span></span>
<span data-ttu-id="53bcd-103">編輯 <xref:System.Data.DataTable> 中的值時，若要避免必須在每次發生資料列錯誤時都回應，則可以將錯誤資訊加入至資料列中，供日後使用。</span><span class="sxs-lookup"><span data-stu-id="53bcd-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="53bcd-104">針對這項用途，<xref:System.Data.DataRow> 物件會為每個資料列提供 <xref:System.Data.DataRow.RowError%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="53bcd-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="53bcd-105">將資料加入至**RowError**屬性**DataRow**設定<xref:System.Data.DataRow.HasErrors%2A>屬性**DataRow**至**true**。</span><span class="sxs-lookup"><span data-stu-id="53bcd-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="53bcd-106">如果**DataRow**屬於**DataTable**，並**DataRow.HasErrors**是**true**， **DataTable.HasErrors**屬性也是 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="53bcd-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="53bcd-107">這同樣適用於**資料集**要**DataTable**所屬。</span><span class="sxs-lookup"><span data-stu-id="53bcd-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="53bcd-108">在測試是否有錯誤時，您可以檢查**HasErrors**屬性來判斷錯誤資訊是否已新增至任何資料列。</span><span class="sxs-lookup"><span data-stu-id="53bcd-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="53bcd-109">如果**HasErrors**是 **，則為 true**，您可以使用<xref:System.Data.DataTable.GetErrors%2A>方法**DataTable**傳回和檢查的錯誤，資料列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="53bcd-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53bcd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53bcd-110">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="53bcd-111">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="53bcd-111">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="53bcd-112">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="53bcd-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
