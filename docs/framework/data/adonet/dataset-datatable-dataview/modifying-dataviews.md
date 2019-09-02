---
title: 修改 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 0b2bfd1b0490572e78c8ce365491a8d48db87684
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204568"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="008ae-102">修改 DataView</span><span class="sxs-lookup"><span data-stu-id="008ae-102">Modifying DataViews</span></span>
<span data-ttu-id="008ae-103">您可以使用 <xref:System.Data.DataView> 加入、刪除或修改基底資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="008ae-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="008ae-104">使用**dataview**修改基礎資料表中資料的能力, 是藉由設定**dataview**的三個布林值屬性之一來控制。</span><span class="sxs-lookup"><span data-stu-id="008ae-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="008ae-105">這些屬性是 <xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> 和 <xref:System.Data.DataView.AllowDelete%2A>。</span><span class="sxs-lookup"><span data-stu-id="008ae-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="008ae-106">預設會將其設定為**true** 。</span><span class="sxs-lookup"><span data-stu-id="008ae-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="008ae-107">如果**AllowNew**為**true**, 您<xref:System.Data.DataView.AddNew%2A>可以使用**DataView**的方法來建立新<xref:System.Data.DataRowView>的。</span><span class="sxs-lookup"><span data-stu-id="008ae-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="008ae-108">請注意, 在呼叫<xref:System.Data.DataTable> **DataRowView**的<xref:System.Data.DataRowView.EndEdit%2A>方法之前, 不會實際將新的資料列加入基礎。</span><span class="sxs-lookup"><span data-stu-id="008ae-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="008ae-109">如果呼叫**DataRowView**的方法,則會捨棄新的資料列。<xref:System.Data.DataRowView.CancelEdit%2A></span><span class="sxs-lookup"><span data-stu-id="008ae-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="008ae-110">另請注意, 您一次只能編輯一個**DataRowView** 。</span><span class="sxs-lookup"><span data-stu-id="008ae-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="008ae-111">如果您在暫止資料列存在時, 呼叫**DataRowView**的**AddNew**或**BeginEdit**方法, 就會在暫止資料列上隱含呼叫**EndEdit** 。</span><span class="sxs-lookup"><span data-stu-id="008ae-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="008ae-112">呼叫**EndEdit**時, 變更會套用至基礎**DataTable** , 之後可以使用**DataTable**、 **DataSet** **的 AcceptChanges 或 RejectChanges 方法來認可或拒絕。DataRow**物件。</span><span class="sxs-lookup"><span data-stu-id="008ae-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="008ae-113">如果**AllowNew**為**false**, 則當您呼叫**DataRowView**的**AddNew**方法時, 就會擲回例外狀況 (exception)。</span><span class="sxs-lookup"><span data-stu-id="008ae-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="008ae-114">如果**AllowEdit**為**true**, 您可以透過**DataRowView**修改**DataRow**的內容。</span><span class="sxs-lookup"><span data-stu-id="008ae-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="008ae-115">您可以使用**DataRowView**來確認基礎資料列的變更, 或使用**DataRowView**來拒絕變更。</span><span class="sxs-lookup"><span data-stu-id="008ae-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="008ae-116">請注意您一次只能編輯一筆資料列。</span><span class="sxs-lookup"><span data-stu-id="008ae-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="008ae-117">如果您在暫止資料列存在時, 呼叫**DataRowView**的**AddNew**或**BeginEdit**方法, 就會在暫止資料列上隱含呼叫**EndEdit** 。</span><span class="sxs-lookup"><span data-stu-id="008ae-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="008ae-118">呼叫**EndEdit**時, 建議的變更會放在基礎**DataRow**的**目前**資料列版本中, 之後可以使用的**AcceptChanges**或**RejectChanges**方法**來認可或拒絕DataTable**、 **DataSet**或**DataRow**物件。</span><span class="sxs-lookup"><span data-stu-id="008ae-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="008ae-119">如果**AllowEdit**為**false**, 如果您嘗試修改**DataView**中的值, 則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="008ae-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="008ae-120">編輯現有的**DataRowView**時, 仍會以建議的變更來引發基礎**DataTable**的事件。</span><span class="sxs-lookup"><span data-stu-id="008ae-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="008ae-121">請注意, 如果您在基礎**DataRow**上呼叫**EndEdit**或**CancelEdit** , 不論**DataRowView**上是否呼叫**EndEdit**或**CancelEdit** , 都會套用或取消暫止的變更。</span><span class="sxs-lookup"><span data-stu-id="008ae-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="008ae-122">如果**AllowDelete**為**true**, 您可以使用**Dataview**或**DataRowView**物件的**delete**方法刪除**dataview**中的資料列, 並從基礎**DataTable**中刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="008ae-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="008ae-123">您稍後可以分別使用**AcceptChanges**或**RejectChanges**來認可或拒絕刪除。</span><span class="sxs-lookup"><span data-stu-id="008ae-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="008ae-124">如果**AllowDelete**為**false**, 則當您呼叫**DataView**或**DataRowView**的**Delete**方法時, 就會擲回例外狀況 (exception)。</span><span class="sxs-lookup"><span data-stu-id="008ae-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="008ae-125">下列程式碼範例會停用使用**dataview**來刪除資料列, 並使用**dataview**將新資料列加入基礎資料表中。</span><span class="sxs-lookup"><span data-stu-id="008ae-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="008ae-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="008ae-126">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="008ae-127">DataView</span><span class="sxs-lookup"><span data-stu-id="008ae-127">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="008ae-128">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="008ae-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
