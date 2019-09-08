---
title: 修改 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3e811410ea9fdd4be0cbd84b895483f69f58b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786051"
---
# <a name="modifying-dataviews"></a>修改 DataView
您可以使用 <xref:System.Data.DataView> 加入、刪除或修改基底資料表中的資料列。 使用**dataview**修改基礎資料表中資料的能力，是藉由設定**dataview**的三個布林值屬性之一來控制。 這些屬性是 <xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> 和 <xref:System.Data.DataView.AllowDelete%2A>。 預設會將其設定為**true** 。  
  
 如果**AllowNew**為**true**，您<xref:System.Data.DataView.AddNew%2A>可以使用**DataView**的方法來建立新<xref:System.Data.DataRowView>的。 請注意，在呼叫<xref:System.Data.DataTable> **DataRowView**的<xref:System.Data.DataRowView.EndEdit%2A>方法之前，不會實際將新的資料列加入基礎。 如果呼叫**DataRowView**的方法，則會捨棄新的資料列。<xref:System.Data.DataRowView.CancelEdit%2A> 另請注意，您一次只能編輯一個**DataRowView** 。 如果您在暫止資料列存在時，呼叫**DataRowView**的**AddNew**或**BeginEdit**方法，就會在暫止資料列上隱含呼叫**EndEdit** 。 呼叫**EndEdit**時，變更會套用至基礎**DataTable** ，之後可以使用**DataTable**、 **DataSet** **的 AcceptChanges 或 RejectChanges 方法來認可或拒絕。DataRow**物件。 如果**AllowNew**為**false**，則當您呼叫**DataRowView**的**AddNew**方法時，就會擲回例外狀況（exception）。  
  
 如果**AllowEdit**為**true**，您可以透過**DataRowView**修改**DataRow**的內容。 您可以使用**DataRowView**來確認基礎資料列的變更，或使用**DataRowView**來拒絕變更。 請注意您一次只能編輯一筆資料列。 如果您在暫止資料列存在時，呼叫**DataRowView**的**AddNew**或**BeginEdit**方法，就會在暫止資料列上隱含呼叫**EndEdit** 。 呼叫**EndEdit**時，建議的變更會放在基礎**DataRow**的**目前**資料列版本中，之後可以使用的**AcceptChanges**或**RejectChanges**方法**來認可或拒絕DataTable**、 **DataSet**或**DataRow**物件。 如果**AllowEdit**為**false**，如果您嘗試修改**DataView**中的值，則會擲回例外狀況。  
  
 編輯現有的**DataRowView**時，仍會以建議的變更來引發基礎**DataTable**的事件。 請注意，如果您在基礎**DataRow**上呼叫**EndEdit**或**CancelEdit** ，不論**DataRowView**上是否呼叫**EndEdit**或**CancelEdit** ，都會套用或取消暫止的變更。  
  
 如果**AllowDelete**為**true**，您可以使用**Dataview**或**DataRowView**物件的**delete**方法刪除**dataview**中的資料列，並從基礎**DataTable**中刪除資料列。 您稍後可以分別使用**AcceptChanges**或**RejectChanges**來認可或拒絕刪除。 如果**AllowDelete**為**false**，則當您呼叫**DataView**或**DataRowView**的**Delete**方法時，就會擲回例外狀況（exception）。  
  
 下列程式碼範例會停用使用**dataview**來刪除資料列，並使用**dataview**將新資料列加入基礎資料表中。  
  
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
- [ADO.NET 概觀](../ado-net-overview.md)
