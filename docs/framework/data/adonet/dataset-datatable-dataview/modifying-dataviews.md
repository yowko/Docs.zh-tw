---
title: 修改 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 8e3a3f92fe8ecc94a041fbcb1540bae18a41dbef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203679"
---
# <a name="modifying-dataviews"></a>修改 DataView

您可以使用 <xref:System.Data.DataView> 加入、刪除或修改基底資料表中的資料列。 使用 **dataview** 修改基礎資料表中資料的能力，是藉由設定 **DataView**的三個布林值屬性中的其中一個來控制。 這些屬性是 <xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> 和 <xref:System.Data.DataView.AllowDelete%2A>。 預設會設定為 **true** 。  
  
 如果 **AllowNew** 為 **true**，您可以使用 <xref:System.Data.DataView.AddNew%2A> **DataView** 的方法來建立新的 <xref:System.Data.DataRowView> 。 請注意，在 <xref:System.Data.DataTable> <xref:System.Data.DataRowView.EndEdit%2A> 呼叫 **DataRowView** 的方法之前，不會實際將新的資料列新增至基礎。 如果 <xref:System.Data.DataRowView.CancelEdit%2A> 呼叫 **DataRowView** 的方法，則會捨棄新的資料列。 另外也請注意，一次只能編輯一個 **DataRowView** 。 如果您在暫止資料列存在時，呼叫**DataRowView**的**AddNew**或**BeginEdit**方法，就會在暫止資料列上隱含呼叫**EndEdit** 。 當**呼叫 EndEdit**時，變更會套用至基礎**DataTable** ，之後可使用**DataTable**、 **DataSet**或**DataRow**物件的**AcceptChanges**或**RejectChanges**方法來認可或拒絕變更。 如果**AllowNew**為**false**，則當您呼叫**DataRowView**的**AddNew**方法時會擲回例外狀況。  
  
 如果**AllowEdit**為**true**，您可以透過**DataRowView**修改**DataRow**的內容。 您可以使用 **DataRowView** 來確認基礎資料列的變更，或使用 **DataRowView CancelEdit**來拒絕變更。 請注意您一次只能編輯一筆資料列。 如果您在暫止資料列存在時，呼叫**DataRowView**的**AddNew**或**BeginEdit**方法，就會在暫止資料列上隱含呼叫**EndEdit** 。 當**呼叫 EndEdit**時，建議的變更會放在基礎**DataRow** **目前**的資料列版本中，之後可使用**DataTable**、 **DataSet**或**DataRow**物件的**AcceptChanges**或**RejectChanges**方法來認可或拒絕。 如果 **AllowEdit** 為 **false**，則當您嘗試修改 **DataView**中的值時，就會擲回例外狀況。  
  
 編輯現有的 **DataRowView** 時，仍會以建議的變更引發基礎 **DataTable** 的事件。 請注意，如果您在基礎**DataRow**上呼叫**EndEdit**或**CancelEdit** ，則不論是否在**DataRowView**上呼叫**EndEdit**或**CancelEdit** ，都會套用或取消暫止的變更。  
  
 如果**AllowDelete**為**true**，您可以使用**Dataview**或**DataRowView**物件的**delete**方法，從**dataview**刪除資料列，然後從基礎**DataTable**中刪除資料列。 您稍後可以分別使用 **AcceptChanges** 或 **RejectChanges** 來認可或拒絕刪除。 如果**AllowDelete**為**false**，則會在您呼叫**DataView**或**DataRowView**的**Delete**方法時擲回例外狀況。  
  
 下列程式碼範例會停用使用 **dataview** 來刪除資料列，並使用 **dataview**將新資料列加入基礎資料表。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataView](dataviews.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
