---
title: DataTable 條件約束
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 254f486fa19d8af30759d9a9fd6642a1a40e82a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034355"
---
# <a name="datatable-constraints"></a><span data-ttu-id="bf25d-102">DataTable 條件約束</span><span class="sxs-lookup"><span data-stu-id="bf25d-102">DataTable Constraints</span></span>
<span data-ttu-id="bf25d-103">您可以使用條件約束，強制使用 <xref:System.Data.DataTable> 中的資料限制，以維持資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="bf25d-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="bf25d-104">條件約束是指套用到資料行或相關資料行的自動規則，當資料列的值變更時，條件約束可決定採取的動作。</span><span class="sxs-lookup"><span data-stu-id="bf25d-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="bf25d-105">會強制執行條件約束時`System.Data.DataSet.EnforceConstraints`的屬性<xref:System.Data.DataSet>是 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="bf25d-106">如需示範如何設定 `EnforceConstraints` 屬性的程式碼範例，請參閱 <xref:System.Data.DataSet.EnforceConstraints%2A> 參考主題。</span><span class="sxs-lookup"><span data-stu-id="bf25d-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="bf25d-107">ADO.NET 有兩種條件約束：<xref:System.Data.ForeignKeyConstraint> 與 <xref:System.Data.UniqueConstraint>。</span><span class="sxs-lookup"><span data-stu-id="bf25d-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="bf25d-108">根據預設，這兩個條件約束會建立時自動建立您所新增的兩個或多個資料表之間的關係<xref:System.Data.DataRelation>要**資料集**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="bf25d-109">不過，您可以停用此行為指定**createConstraints** = **false**時建立關聯。</span><span class="sxs-lookup"><span data-stu-id="bf25d-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="bf25d-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="bf25d-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="bf25d-111">A **ForeignKeyConstraint**會強制執行規則的相關更新與刪除導引到相關資料表的傳播方式。</span><span class="sxs-lookup"><span data-stu-id="bf25d-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="bf25d-112">例如，如果更新或刪除，一個資料表的資料列中的值和相同的值也會在其中一個或多個相關資料表**ForeignKeyConstraint**判斷相關資料表中發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="bf25d-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="bf25d-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>並<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>的屬性**ForeignKeyConstraint**定義當使用者嘗試刪除或更新相關資料表中的資料列時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="bf25d-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="bf25d-114">下表描述不同的設定可供**DeleteRule**並**UpdateRule**的屬性**ForeignKeyConstraint**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="bf25d-115">規則設定</span><span class="sxs-lookup"><span data-stu-id="bf25d-115">Rule setting</span></span>|<span data-ttu-id="bf25d-116">描述</span><span class="sxs-lookup"><span data-stu-id="bf25d-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="bf25d-117">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="bf25d-117">**Cascade**</span></span>|<span data-ttu-id="bf25d-118">刪除或更新關聯資料列。</span><span class="sxs-lookup"><span data-stu-id="bf25d-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="bf25d-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="bf25d-119">**SetNull**</span></span>|<span data-ttu-id="bf25d-120">相關資料列中設定的值**DBNull**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="bf25d-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="bf25d-121">**SetDefault**</span></span>|<span data-ttu-id="bf25d-122">將關聯資料列中的值設為預設值。</span><span class="sxs-lookup"><span data-stu-id="bf25d-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="bf25d-123">**無**</span><span class="sxs-lookup"><span data-stu-id="bf25d-123">**None**</span></span>|<span data-ttu-id="bf25d-124">不對關聯資料列採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="bf25d-124">Take no action on related rows.</span></span> <span data-ttu-id="bf25d-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="bf25d-125">This is the default.</span></span>|  
  
 <span data-ttu-id="bf25d-126">A **ForeignKeyConstraint**可以限制，請變更，以及傳播，相關資料行。</span><span class="sxs-lookup"><span data-stu-id="bf25d-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="bf25d-127">根據設定的屬性**ForeignKeyConstraint**資料行，如果**EnforceConstraints**屬性**資料集**是**true**，在父資料列上執行特定作業時，會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf25d-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="bf25d-128">例如，如果**DeleteRule**屬性**ForeignKeyConstraint**會**None**，無法刪除父資料列，如果有任何子資料列。</span><span class="sxs-lookup"><span data-stu-id="bf25d-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="bf25d-129">您可以建立的外部索引鍵的條件約束所使用的資料行陣列之間或單一資料行之間**ForeignKeyConstraint**建構函式。</span><span class="sxs-lookup"><span data-stu-id="bf25d-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="bf25d-130">將產生**ForeignKeyConstraint**物件**新增**資料表的方法**條件約束**屬性，這是**ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="bf25d-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="bf25d-131">您也可以將建構函式引數傳遞至數個多載**新增**方法**ConstraintCollection**來建立**ForeignKeyConstraint**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="bf25d-132">建立時**ForeignKeyConstraint**，您可以傳遞**DeleteRule**並**UpdateRule**值建構函式做為引數，或者您可以將它們設定為中的屬性下列範例 (其中**DeleteRule**值設定為**無**)。</span><span class="sxs-lookup"><span data-stu-id="bf25d-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="bf25d-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="bf25d-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="bf25d-134">資料列的變更可以使用接受**AcceptChanges**方法，或已取消使用**RejectChanges**方法**資料集**， **DataTable**，或**DataRow**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="bf25d-135">當**資料集**包含**ForeignKeyConstraints**、 叫用**AcceptChanges**或是**RejectChanges**方法會強制**AcceptRejectRule**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="bf25d-136">**AcceptRejectRule**屬性**ForeignKeyConstraint**對子系不會採取哪些動作會決定資料列時**AcceptChanges**或**RejectChanges**父資料列上呼叫。</span><span class="sxs-lookup"><span data-stu-id="bf25d-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="bf25d-137">下表列出可用的設定**AcceptRejectRule**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="bf25d-138">規則設定</span><span class="sxs-lookup"><span data-stu-id="bf25d-138">Rule setting</span></span>|<span data-ttu-id="bf25d-139">描述</span><span class="sxs-lookup"><span data-stu-id="bf25d-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="bf25d-140">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="bf25d-140">**Cascade**</span></span>|<span data-ttu-id="bf25d-141">接受或拒絕子資料列的變更。</span><span class="sxs-lookup"><span data-stu-id="bf25d-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="bf25d-142">**無**</span><span class="sxs-lookup"><span data-stu-id="bf25d-142">**None**</span></span>|<span data-ttu-id="bf25d-143">不對子資料列採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="bf25d-143">Take no action on child rows.</span></span> <span data-ttu-id="bf25d-144">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="bf25d-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="bf25d-145">範例</span><span class="sxs-lookup"><span data-stu-id="bf25d-145">Example</span></span>  
 <span data-ttu-id="bf25d-146">下列範例會建立 <xref:System.Data.ForeignKeyConstraint>、設定其某些屬性 (包括 <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>)，並將它加入 <xref:System.Data.ConstraintCollection> 物件的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="bf25d-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="bf25d-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="bf25d-147">UniqueConstraint</span></span>  
 <span data-ttu-id="bf25d-148">**UniqueConstraint**物件，您可以為單一資料行或陣列中的資料行指派**DataTable**，可確保在指定的資料行或資料行中的所有資料都是唯一每個資料列。</span><span class="sxs-lookup"><span data-stu-id="bf25d-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="bf25d-149">您可以使用，以建立唯一的條件約束的資料行或資料行陣列**UniqueConstraint**建構函式。</span><span class="sxs-lookup"><span data-stu-id="bf25d-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="bf25d-150">將產生**UniqueConstraint**物件**新增**資料表的方法**條件約束**屬性，這是**ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="bf25d-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="bf25d-151">您也可以將建構函式引數傳遞至數個多載**新增**方法**ConstraintCollection**來建立**UniqueConstraint**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="bf25d-152">建立時**UniqueConstraint**資料行或資料行，您可以選擇性地指定資料行或資料行是主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bf25d-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="bf25d-153">您也可以藉由設定來建立資料行的唯一條件約束**Unique**屬性的資料行 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="bf25d-154">或者，設定**Unique**屬性的單一資料行**false**移除可能存在的任何唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="bf25d-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="bf25d-155">如果將一個或多個資料行定義為資料表的主索引鍵，將會自動為指定的一個或多個資料行建立唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="bf25d-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="bf25d-156">如果您移除的資料行**PrimaryKey**屬性**DataTable**，則**UniqueConstraint**已移除。</span><span class="sxs-lookup"><span data-stu-id="bf25d-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="bf25d-157">下列範例會建立**UniqueConstraint**的兩個資料行**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="bf25d-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf25d-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf25d-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="bf25d-159">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="bf25d-159">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="bf25d-160">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="bf25d-160">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="bf25d-161">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="bf25d-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
