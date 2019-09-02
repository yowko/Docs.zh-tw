---
title: DataTable 條件約束
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 68b99e834428261d59c5fb27277b24eb0f6e77e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205059"
---
# <a name="datatable-constraints"></a><span data-ttu-id="9aaec-102">DataTable 條件約束</span><span class="sxs-lookup"><span data-stu-id="9aaec-102">DataTable Constraints</span></span>
<span data-ttu-id="9aaec-103">您可以使用條件約束，強制使用 <xref:System.Data.DataTable> 中的資料限制，以維持資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="9aaec-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="9aaec-104">條件約束是指套用到資料行或相關資料行的自動規則，當資料列的值變更時，條件約束可決定採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9aaec-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="9aaec-105">當的`System.Data.DataSet.EnforceConstraints`屬性<xref:System.Data.DataSet>為**true**時, 就會強制執行條件約束。</span><span class="sxs-lookup"><span data-stu-id="9aaec-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="9aaec-106">如需示範如何設定 `EnforceConstraints` 屬性的程式碼範例，請參閱 <xref:System.Data.DataSet.EnforceConstraints%2A> 參考主題。</span><span class="sxs-lookup"><span data-stu-id="9aaec-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="9aaec-107">ADO.NET 有兩種條件約束：<xref:System.Data.ForeignKeyConstraint> 與 <xref:System.Data.UniqueConstraint>。</span><span class="sxs-lookup"><span data-stu-id="9aaec-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="9aaec-108">根據預設, 當您藉由將加入<xref:System.Data.DataRelation>至**資料集**, 建立兩個或多個資料表之間的關聯性時, 會自動建立這兩個條件約束。</span><span class="sxs-lookup"><span data-stu-id="9aaec-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="9aaec-109">不過, 您可以在建立關聯性時指定**createConstraints**  =  **false**來停用此行為。</span><span class="sxs-lookup"><span data-stu-id="9aaec-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="9aaec-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="9aaec-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="9aaec-111">**ForeignKeyConstraint**會強制執行有關如何傳播更新和刪除相關資料表的規則。</span><span class="sxs-lookup"><span data-stu-id="9aaec-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="9aaec-112">例如, 如果一個資料表的資料列中的值已更新或刪除, 而且相同的值也用於一個或多個相關的資料表中, 則**ForeignKeyConstraint**會決定相關資料表中發生的情況。</span><span class="sxs-lookup"><span data-stu-id="9aaec-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="9aaec-113">ForeignKeyConstraint <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>的<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>和屬性會定義當使用者嘗試刪除或更新相關資料表中的資料列時, 所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9aaec-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="9aaec-114">下表說明**ForeignKeyConstraint**的**DeleteRule**和**UpdateRule**屬性可用的不同設定。</span><span class="sxs-lookup"><span data-stu-id="9aaec-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="9aaec-115">規則設定</span><span class="sxs-lookup"><span data-stu-id="9aaec-115">Rule setting</span></span>|<span data-ttu-id="9aaec-116">描述</span><span class="sxs-lookup"><span data-stu-id="9aaec-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="9aaec-117">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="9aaec-117">**Cascade**</span></span>|<span data-ttu-id="9aaec-118">刪除或更新關聯資料列。</span><span class="sxs-lookup"><span data-stu-id="9aaec-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="9aaec-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="9aaec-119">**SetNull**</span></span>|<span data-ttu-id="9aaec-120">將相關資料列中的值設定為**DBNull**。</span><span class="sxs-lookup"><span data-stu-id="9aaec-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="9aaec-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="9aaec-121">**SetDefault**</span></span>|<span data-ttu-id="9aaec-122">將關聯資料列中的值設為預設值。</span><span class="sxs-lookup"><span data-stu-id="9aaec-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="9aaec-123">**無**</span><span class="sxs-lookup"><span data-stu-id="9aaec-123">**None**</span></span>|<span data-ttu-id="9aaec-124">不對關聯資料列採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="9aaec-124">Take no action on related rows.</span></span> <span data-ttu-id="9aaec-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9aaec-125">This is the default.</span></span>|  
  
 <span data-ttu-id="9aaec-126">**ForeignKeyConstraint**可以限制及傳播相關資料行的變更。</span><span class="sxs-lookup"><span data-stu-id="9aaec-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="9aaec-127">視資料行的**ForeignKeyConstraint**所設定的屬性而定, 如果 DataSet 的**EnforceConstraints**屬性為**True**, 則在父**資料**列上執行某些作業將會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9aaec-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="9aaec-128">例如, 如果**ForeignKeyConstraint**的**DeleteRule**屬性為**None**, 則父資料列若有任何子資料列, 就無法刪除。</span><span class="sxs-lookup"><span data-stu-id="9aaec-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="9aaec-129">您可以使用**ForeignKeyConstraint**的函式, 在單一資料行之間或資料行陣列之間建立外鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="9aaec-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="9aaec-130">將產生的**ForeignKeyConstraint**物件傳遞給資料表的**條件約束**屬性的**Add**方法, 也就是**ConstraintCollection**。</span><span class="sxs-lookup"><span data-stu-id="9aaec-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="9aaec-131">您也可以將函式引數傳遞給**ConstraintCollection**的**Add**方法的數個多載, 以建立**ForeignKeyConstraint**。</span><span class="sxs-lookup"><span data-stu-id="9aaec-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="9aaec-132">建立**ForeignKeyConstraint**時, 您可以將**DeleteRule**和**UpdateRule**值當做引數傳遞至函式, 也可以將它們設定為屬性, 如下列範例所示 (其中**DeleteRule**值設定為**無**)。</span><span class="sxs-lookup"><span data-stu-id="9aaec-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
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
  
### <a name="acceptrejectrule"></a><span data-ttu-id="9aaec-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="9aaec-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="9aaec-134">您可以使用**AcceptChanges**方法來接受**資料**列的變更, 或使用 DataSet、 **DataTable**或**DataRow**的**RejectChanges**方法來取消。</span><span class="sxs-lookup"><span data-stu-id="9aaec-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="9aaec-135">當**資料集**包含**ForeignKeyConstraints**時, 叫**用 AcceptChanges**或**RejectChanges**方法會強制執行**AcceptRejectRule**。</span><span class="sxs-lookup"><span data-stu-id="9aaec-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="9aaec-136">**ForeignKeyConstraint**的**AcceptRejectRule**屬性會決定在父資料列上呼叫**AcceptChanges**或**RejectChanges**時, 將對子資料列採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9aaec-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="9aaec-137">下表列出**AcceptRejectRule**的可用設定。</span><span class="sxs-lookup"><span data-stu-id="9aaec-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="9aaec-138">規則設定</span><span class="sxs-lookup"><span data-stu-id="9aaec-138">Rule setting</span></span>|<span data-ttu-id="9aaec-139">描述</span><span class="sxs-lookup"><span data-stu-id="9aaec-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="9aaec-140">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="9aaec-140">**Cascade**</span></span>|<span data-ttu-id="9aaec-141">接受或拒絕子資料列的變更。</span><span class="sxs-lookup"><span data-stu-id="9aaec-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="9aaec-142">**無**</span><span class="sxs-lookup"><span data-stu-id="9aaec-142">**None**</span></span>|<span data-ttu-id="9aaec-143">不對子資料列採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="9aaec-143">Take no action on child rows.</span></span> <span data-ttu-id="9aaec-144">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9aaec-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="9aaec-145">範例</span><span class="sxs-lookup"><span data-stu-id="9aaec-145">Example</span></span>  
 <span data-ttu-id="9aaec-146">下列範例會建立 <xref:System.Data.ForeignKeyConstraint>、設定其某些屬性 (包括 <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>)，並將它加入 <xref:System.Data.ConstraintCollection> 物件的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="9aaec-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="9aaec-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="9aaec-147">UniqueConstraint</span></span>  
 <span data-ttu-id="9aaec-148">**UniqueConstraint**物件, 可以指派至單一資料行或**DataTable**中的資料行陣列, 以確保指定之資料行中的所有資料在每一列中都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9aaec-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="9aaec-149">您可以使用**UniqueConstraint**的函式, 為數據行或資料行陣列建立唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="9aaec-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="9aaec-150">將產生的**UniqueConstraint**物件傳遞給資料表的**條件約束**屬性的**Add**方法, 也就是**ConstraintCollection**。</span><span class="sxs-lookup"><span data-stu-id="9aaec-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="9aaec-151">您也可以將函式引數傳遞給**ConstraintCollection**的**Add**方法的數個多載, 以建立**UniqueConstraint**。</span><span class="sxs-lookup"><span data-stu-id="9aaec-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="9aaec-152">建立一或多個資料行的**UniqueConstraint**時, 您可以選擇性地指定資料行是否為主鍵。</span><span class="sxs-lookup"><span data-stu-id="9aaec-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="9aaec-153">您也可以將資料行的**unique**屬性設定為**true**, 以建立資料行的唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="9aaec-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="9aaec-154">或者, 將單一資料行的**unique**屬性設定為**false** , 會移除可能存在的任何 Unique 條件約束。</span><span class="sxs-lookup"><span data-stu-id="9aaec-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="9aaec-155">如果將一個或多個資料行定義為資料表的主索引鍵，將會自動為指定的一個或多個資料行建立唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="9aaec-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="9aaec-156">如果您從**DataTable**的**PrimaryKey**屬性中移除資料行, 則會移除**UniqueConstraint** 。</span><span class="sxs-lookup"><span data-stu-id="9aaec-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="9aaec-157">下列範例會針對**DataTable**的兩個數據行建立**UniqueConstraint** 。</span><span class="sxs-lookup"><span data-stu-id="9aaec-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9aaec-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9aaec-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="9aaec-159">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="9aaec-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="9aaec-160">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="9aaec-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="9aaec-161">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="9aaec-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
