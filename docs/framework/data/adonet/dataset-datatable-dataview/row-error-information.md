---
title: 資料列錯誤資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 8673b7fbc2e4238f7047698376c53af991de9f1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181163"
---
# <a name="row-error-information"></a><span data-ttu-id="2105a-102">資料列錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="2105a-102">Row Error Information</span></span>

<span data-ttu-id="2105a-103">編輯 <xref:System.Data.DataTable> 中的值時，若要避免必須在每次發生資料列錯誤時都回應，則可以將錯誤資訊加入至資料列中，供日後使用。</span><span class="sxs-lookup"><span data-stu-id="2105a-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="2105a-104">針對這項用途，<xref:System.Data.DataRow> 物件會為每個資料列提供 <xref:System.Data.DataRow.RowError%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="2105a-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="2105a-105">將資料加入至**datarow**的**RowError**屬性時，會將 <xref:System.Data.DataRow.HasErrors%2A> **DataRow**的屬性設定為**true**。</span><span class="sxs-lookup"><span data-stu-id="2105a-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="2105a-106">如果 **datarow** 是 **DataTable**的一部分，且 **HasErrors** 為 **true**，則 **DataTable. HasErrors** 屬性也是 **true**。</span><span class="sxs-lookup"><span data-stu-id="2105a-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="2105a-107">這也適用于**DataTable**所屬的**資料集**。</span><span class="sxs-lookup"><span data-stu-id="2105a-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="2105a-108">測試錯誤時，您可以檢查 **HasErrors** 屬性，以判斷是否已將錯誤資訊加入至任何資料列。</span><span class="sxs-lookup"><span data-stu-id="2105a-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="2105a-109">如果 **HasErrors** 為 **true**，您可以使用 <xref:System.Data.DataTable.GetErrors%2A> **DataTable** 的方法來傳回和檢查具有錯誤的資料列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2105a-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2105a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2105a-110">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="2105a-111">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="2105a-111">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- <span data-ttu-id="2105a-112">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="2105a-112">[ADO.NET Overview](../ado-net-overview.md)</span></span>
