---
title: DataTable 條件約束
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151282"
---
# <a name="datatable-constraints"></a><span data-ttu-id="56692-102">DataTable 條件約束</span><span class="sxs-lookup"><span data-stu-id="56692-102">DataTable Constraints</span></span>
<span data-ttu-id="56692-103">您可以使用條件約束，強制使用 <xref:System.Data.DataTable> 中的資料限制，以維持資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="56692-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="56692-104">條件約束是指套用到資料行或相關資料行的自動規則，當資料列的值變更時，條件約束可決定採取的動作。</span><span class="sxs-lookup"><span data-stu-id="56692-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="56692-105">當 的屬性`System.Data.DataSet.EnforceConstraints`<xref:System.Data.DataSet>**為 true**時，將強制執行約束。</span><span class="sxs-lookup"><span data-stu-id="56692-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="56692-106">如需示範如何設定 `EnforceConstraints` 屬性的程式碼範例，請參閱 <xref:System.Data.DataSet.EnforceConstraints%2A> 參考主題。</span><span class="sxs-lookup"><span data-stu-id="56692-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="56692-107">ADO.NET 有兩種條件約束：<xref:System.Data.ForeignKeyConstraint> 與 <xref:System.Data.UniqueConstraint>。</span><span class="sxs-lookup"><span data-stu-id="56692-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="56692-108">預設情況下，當您通過向<xref:System.Data.DataRelation>**DataSet**添加 創建 兩個或多個表之間的關係時，將自動創建這兩個約束。</span><span class="sxs-lookup"><span data-stu-id="56692-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="56692-109">但是，您可以通過在創建關係時指定**創建約束** = **為 false**來禁用此行為。</span><span class="sxs-lookup"><span data-stu-id="56692-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="56692-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="56692-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="56692-111">**外鍵約束**強制實施有關如何傳播相關表的更新和刪除的規則。</span><span class="sxs-lookup"><span data-stu-id="56692-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="56692-112">例如，如果更新或刪除一個表行中的值，並且同一值也用於一個或多個相關表，**則外鍵約束**將確定相關表中發生的情況。</span><span class="sxs-lookup"><span data-stu-id="56692-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="56692-113">**外鍵約束**的<xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>和<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>屬性定義使用者嘗試刪除或更新相關表中的行時要執行的操作。</span><span class="sxs-lookup"><span data-stu-id="56692-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="56692-114">下表描述了**外鍵約束**的**DeleteRule**和**UpdateRule**屬性可用的不同設置。</span><span class="sxs-lookup"><span data-stu-id="56692-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="56692-115">規則設定</span><span class="sxs-lookup"><span data-stu-id="56692-115">Rule setting</span></span>|<span data-ttu-id="56692-116">描述</span><span class="sxs-lookup"><span data-stu-id="56692-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="56692-117">**級 聯**</span><span class="sxs-lookup"><span data-stu-id="56692-117">**Cascade**</span></span>|<span data-ttu-id="56692-118">刪除或更新關聯資料列。</span><span class="sxs-lookup"><span data-stu-id="56692-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="56692-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="56692-119">**SetNull**</span></span>|<span data-ttu-id="56692-120">將相關行中的值設置為**DBNull**。</span><span class="sxs-lookup"><span data-stu-id="56692-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="56692-121">**設置預設值**</span><span class="sxs-lookup"><span data-stu-id="56692-121">**SetDefault**</span></span>|<span data-ttu-id="56692-122">將關聯資料列中的值設為預設值。</span><span class="sxs-lookup"><span data-stu-id="56692-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="56692-123">**無**</span><span class="sxs-lookup"><span data-stu-id="56692-123">**None**</span></span>|<span data-ttu-id="56692-124">不對關聯資料列採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="56692-124">Take no action on related rows.</span></span> <span data-ttu-id="56692-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="56692-125">This is the default.</span></span>|  
  
 <span data-ttu-id="56692-126">**外鍵約束**可以限制並傳播對相關列的更改。</span><span class="sxs-lookup"><span data-stu-id="56692-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="56692-127">根據為列的**外鍵約束**設置的屬性，如果**DataSet**的**強制約束**屬性**為 true，** 則對父行執行某些操作將導致異常。</span><span class="sxs-lookup"><span data-stu-id="56692-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="56692-128">例如，如果**外鍵約束**的**DeleteRule**屬性為 **"無**"，則如果父行具有任何子行，則無法刪除該行。</span><span class="sxs-lookup"><span data-stu-id="56692-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="56692-129">可以使用**外鍵約束**建構函式在單個列之間或列陣列之間創建外鍵約束。</span><span class="sxs-lookup"><span data-stu-id="56692-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="56692-130">將生成的**外鍵約束**物件傳遞給**表的約束屬性**的**Add**方法，該方法是**約束集合**。</span><span class="sxs-lookup"><span data-stu-id="56692-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="56692-131">還可以將建構函式參數傳遞給**約束集合**的**Add**方法的幾個重載，以創建**外鍵約束**。</span><span class="sxs-lookup"><span data-stu-id="56692-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="56692-132">創建**外鍵約束**時，可以將**DeleteRule**和**UpdateRule**值作為參數傳遞給建構函式，也可以將它們設置為屬性，如以下示例（其中**DeleteRule**值設置為 **"無**" ）。</span><span class="sxs-lookup"><span data-stu-id="56692-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
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
  
### <a name="acceptrejectrule"></a><span data-ttu-id="56692-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="56692-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="56692-134">可以使用 **"接受更改**"方法接受對行的更改，或使用**資料集**、**資料表**或 DataRow 的**拒絕更改**方法取消對行**的更改**。</span><span class="sxs-lookup"><span data-stu-id="56692-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="56692-135">當**資料集**包含**外鍵約束**時，調用 **"接受更改**"或 **"拒絕更改"** 方法將強制執行 **"接受拒絕規則**"。</span><span class="sxs-lookup"><span data-stu-id="56692-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="56692-136">**外鍵約束**的 **"接受拒絕規則"** 屬性確定在父行上調用 **"接受更改**"或 **"拒絕更改**"時將對子行執行哪些操作。</span><span class="sxs-lookup"><span data-stu-id="56692-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="56692-137">下表列出了 **"接受拒絕規則**"的可用設置。</span><span class="sxs-lookup"><span data-stu-id="56692-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="56692-138">規則設定</span><span class="sxs-lookup"><span data-stu-id="56692-138">Rule setting</span></span>|<span data-ttu-id="56692-139">描述</span><span class="sxs-lookup"><span data-stu-id="56692-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="56692-140">**級 聯**</span><span class="sxs-lookup"><span data-stu-id="56692-140">**Cascade**</span></span>|<span data-ttu-id="56692-141">接受或拒絕子資料列的變更。</span><span class="sxs-lookup"><span data-stu-id="56692-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="56692-142">**無**</span><span class="sxs-lookup"><span data-stu-id="56692-142">**None**</span></span>|<span data-ttu-id="56692-143">不對子資料列採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="56692-143">Take no action on child rows.</span></span> <span data-ttu-id="56692-144">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="56692-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="56692-145">範例</span><span class="sxs-lookup"><span data-stu-id="56692-145">Example</span></span>  
 <span data-ttu-id="56692-146">下列範例會建立 <xref:System.Data.ForeignKeyConstraint>、設定其某些屬性 (包括 <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>)，並將它加入 <xref:System.Data.ConstraintCollection> 物件的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="56692-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="56692-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="56692-147">UniqueConstraint</span></span>  
 <span data-ttu-id="56692-148">**唯一約束**物件可以分配給單個列或**DataTable**中的列陣列，可確保指定列或列中的所有資料每行都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="56692-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="56692-149">可以使用**唯一約束**建構函式為列或列陣列創建唯一約束。</span><span class="sxs-lookup"><span data-stu-id="56692-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="56692-150">將生成的**唯一約束**物件傳遞給**表的約束屬性**的**Add**方法，該方法是**約束集合**。</span><span class="sxs-lookup"><span data-stu-id="56692-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="56692-151">還可以將建構函式參數傳遞給**約束集合**的**Add**方法的幾個重載，以創建**唯一約束**。</span><span class="sxs-lookup"><span data-stu-id="56692-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="56692-152">為列或列創建**唯一約束**時，可以選擇指定列或列是主鍵。</span><span class="sxs-lookup"><span data-stu-id="56692-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="56692-153">還可以通過將列**的唯一**屬性設置為**true，** 為列創建唯一約束。</span><span class="sxs-lookup"><span data-stu-id="56692-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="56692-154">或者，將單個列**的唯一**屬性設置為**false**將刪除可能存在的任何唯一約束。</span><span class="sxs-lookup"><span data-stu-id="56692-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="56692-155">如果將一個或多個資料行定義為資料表的主索引鍵，將會自動為指定的一個或多個資料行建立唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="56692-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="56692-156">如果從**DataTable\*\*\*\*的主鍵**屬性中刪除列，則將刪除**唯一約束**。</span><span class="sxs-lookup"><span data-stu-id="56692-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="56692-157">下面的示例為**DataTable**的兩列創建**唯一約束**。</span><span class="sxs-lookup"><span data-stu-id="56692-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56692-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56692-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="56692-159">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="56692-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="56692-160">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="56692-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="56692-161">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="56692-161">[ADO.NET Overview](../ado-net-overview.md)</span></span>
