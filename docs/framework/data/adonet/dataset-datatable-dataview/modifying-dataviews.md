---
title: 修改 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3b1e0cbfc6118ad9ca670f5d91183b78b2c99d89
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845017"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="c8cb8-102">修改 DataView</span><span class="sxs-lookup"><span data-stu-id="c8cb8-102">Modifying DataViews</span></span>
<span data-ttu-id="c8cb8-103">您可以使用 <xref:System.Data.DataView> 加入、刪除或修改基底資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="c8cb8-104">若要使用的能力**DataView**修改基礎資料表中的資料由控制設定的三個布林值屬性的其中一個**DataView**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="c8cb8-105">這些屬性是 <xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> 和 <xref:System.Data.DataView.AllowDelete%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="c8cb8-106">它們會設定為 **，則為 true**預設。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="c8cb8-107">如果**AllowNew**是 **，則為 true**，您可以使用<xref:System.Data.DataView.AddNew%2A>方法**DataView**來建立新的<xref:System.Data.DataRowView>。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="c8cb8-108">請注意，新的資料列不是實際新增至基礎<xref:System.Data.DataTable>直到<xref:System.Data.DataRowView.EndEdit%2A>方法**DataRowView**呼叫。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="c8cb8-109">如果<xref:System.Data.DataRowView.CancelEdit%2A>方法**DataRowView**是呼叫，則會捨棄新的資料列。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="c8cb8-110">也請注意，您可以編輯其中之一**DataRowView**一次。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="c8cb8-111">如果您呼叫**AddNew**或是**BeginEdit**方法**DataRowView**暫止的資料列存在時， **EndEdit**上隱含呼叫暫止的資料列。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="c8cb8-112">當**EndEdit**是呼叫，所做的變更套用至基礎**DataTable**而且可以稍後再認可或拒絕使用**AcceptChanges**或**RejectChanges**方法**DataTable**， **DataSet**，或**DataRow**物件。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="c8cb8-113">如果**AllowNew**是**false**，如果您呼叫會擲回例外狀況**AddNew**方法**DataRowView**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="c8cb8-114">如果**AllowEdit**是 **，則為 true**，您可以修改的內容**DataRow**透過**DataRowView**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="c8cb8-115">您可以確認變更為基礎的資料列使用**DataRowView.EndEdit**或拒絕變更**DataRowView.CancelEdit**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="c8cb8-116">請注意您一次只能編輯一筆資料列。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="c8cb8-117">如果您呼叫**AddNew**或是**BeginEdit**方法**DataRowView**暫止的資料列存在時， **EndEdit**上隱含呼叫暫止的資料列。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="c8cb8-118">當**EndEdit**呼叫時，建議的變更會放在**目前**基礎的資料列版本**DataRow**而且可以稍後再認可或拒絕使用**AcceptChanges**或是**RejectChanges**種**DataTable**， **DataSet**，或**DataRow**物件。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="c8cb8-119">如果**AllowEdit**是**false**，如果您嘗試修改中的值，會擲回例外狀況**DataView**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="c8cb8-120">當現有**DataRowView**正在編輯中，基礎事件**DataTable**仍會引發與建議的變更。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="c8cb8-121">請注意，如果您呼叫**EndEdit**或**CancelEdit**於基礎**DataRow**、 暫止變更將套用或取消無論**EndEdit**或是**CancelEdit**上呼叫**DataRowView**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="c8cb8-122">如果**AllowDelete**是 **，則為 true**，您可以刪除資料列，從**DataView**利用**刪除**方法**DataView**或是**DataRowView**物件和資料列會刪除基礎**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="c8cb8-123">您可以稍後再認可或拒絕使用刪除**AcceptChanges**或是**RejectChanges**分別。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="c8cb8-124">如果**AllowDelete**是**false**，如果您呼叫會擲回例外狀況**刪除**方法**DataView**或**DataRowView**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="c8cb8-125">下列程式碼範例會停用使用**DataView**若要刪除的資料列，並將新的資料列加入至基礎的資料表使用**DataView**。</span><span class="sxs-lookup"><span data-stu-id="c8cb8-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8cb8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8cb8-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="c8cb8-127">DataView</span><span class="sxs-lookup"><span data-stu-id="c8cb8-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="c8cb8-128">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c8cb8-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
