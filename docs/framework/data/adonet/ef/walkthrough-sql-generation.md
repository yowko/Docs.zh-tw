---
title: 逐步解說：SQL 產生
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 09b5a3c2dea5cd0483d617ee8064b41dc19c3374
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248282"
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="63fee-102">逐步解說：SQL 產生</span><span class="sxs-lookup"><span data-stu-id="63fee-102">Walkthrough: SQL Generation</span></span>

<span data-ttu-id="63fee-103">本主題說明 SQL 產生如何發生在[範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)中。</span><span class="sxs-lookup"><span data-stu-id="63fee-103">This topic illustrates how SQL generation occurs in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0).</span></span> <span data-ttu-id="63fee-104">下列 Entity SQL 查詢會使用範例提供者所隨附的模型：</span><span class="sxs-lookup"><span data-stu-id="63fee-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

<span data-ttu-id="63fee-105">此查詢會產生傳遞給提供者的下列輸出命令樹：</span><span class="sxs-lookup"><span data-stu-id="63fee-105">The query produces the following output command tree that is passed to the provider:</span></span>

```
DbQueryCommandTree
|_Parameters
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}
  |_Project
    |_Input : 'Join4'
    | |_InnerJoin
    |   |_Left : 'Join1'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent1'
    |   |   | |_Scan : dbo.Products
    |   |   |_Right : 'Extent2'
    |   |   | |_Scan : dbo.Categories
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent1).CategoryID
    |   |       |_=
    |   |       |_Var(Extent2).CategoryID
    |   |_Right : 'Join3'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent3'
    |   |   | |_Scan : dbo.OrderDetails
    |   |   |_Right : 'Join2'
    |   |   | |_LeftOuterJoin
    |   |   |   |_Left : 'Extent4'
    |   |   |   | |_Scan : dbo.Orders
    |   |   |   |_Right : 'Extent5'
    |   |   |   | |_Scan : dbo.InternationalOrders
    |   |   |   |_JoinCondition
    |   |   |     |_
    |   |   |       |_Var(Extent4).OrderID
    |   |   |       |_=
    |   |   |       |_Var(Extent5).OrderID
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent3).OrderID
    |   |       |_=
    |   |       |_Var(Join2).Extent4.OrderID
    |   |_JoinCondition
    |     |_
    |       |_Var(Join1).Extent1.ProductID
    |       |_=
    |       |_Var(Join3).Extent3.ProductID
    |_Projection
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]
        |_Column : 'C1'
        | |_1
        |_Column : 'ProductID'
        | |_Var(Join4).Join1.Extent1.ProductID
        |_Column : 'ProductName'
        | |_Var(Join4).Join1.Extent1.ProductName
        |_Column : 'CategoryName'
        | |_Var(Join4).Join1.Extent2.CategoryName
        |_Column : 'ShipCountry'
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry
        |_Column : 'ProductID1'
          |_Var(Join4).Join3.Extent3.ProductID
```

 <span data-ttu-id="63fee-106">本主題描述如何將這個輸出命令樹轉譯為下列 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="63fee-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>

```sql
SELECT
1 AS [C1],
[Extent1].[ProductID] AS [ProductID],
[Extent1].[ProductName] AS [ProductName],
[Extent2].[CategoryName] AS [CategoryName],
[Join3].[ShipCountry] AS [ShipCountry],
[Join3].[ProductID] AS [ProductID1]
FROM   [dbo].[Products] AS [Extent1]
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]
INNER JOIN
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]
FROM  [dbo].[OrderDetails] AS [Extent3]
LEFT OUTER JOIN
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]
FROM  [dbo].[Orders] AS [Extent4]
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]
```

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="63fee-107">SQL 產生的第一個階段:造訪運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="63fee-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="63fee-108">下圖說明造訪者的最初空白狀態。</span><span class="sxs-lookup"><span data-stu-id="63fee-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="63fee-109">在整個主題中，只會顯示與逐步解說有關的屬性。</span><span class="sxs-lookup"><span data-stu-id="63fee-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>

<span data-ttu-id="63fee-110">![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="63fee-110">![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>

<span data-ttu-id="63fee-111">當瀏覽專案節點時，VisitInputExpression 會在它的輸入 (Join4) 上呼叫，這樣會由 VisitJoinExpression 方法觸發 Join4 的瀏覽。</span><span class="sxs-lookup"><span data-stu-id="63fee-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="63fee-112">因為這是最上層的聯結，所以 IsParentAJoin 會傳回 false，而且新的 SqlSelectStatement (SelectStatement0) 會建立並推送到 SELECT 陳述式堆疊上。</span><span class="sxs-lookup"><span data-stu-id="63fee-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="63fee-113">此外，新的範圍 (scope0) 也會輸入符號表中。</span><span class="sxs-lookup"><span data-stu-id="63fee-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="63fee-114">在瀏覽聯結的第一個 (左邊) 輸入之前，'true' 會推送到 IsParentAJoin 堆疊上。</span><span class="sxs-lookup"><span data-stu-id="63fee-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="63fee-115">在瀏覽 Join1 (這是 Join4 的左邊輸入) 之前，造訪者的狀態會顯示在下一個圖中。</span><span class="sxs-lookup"><span data-stu-id="63fee-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>

<span data-ttu-id="63fee-116">![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="63fee-116">![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>

<span data-ttu-id="63fee-117">當透過 Join4 叫用聯結造訪方法時，IsParentAJoin 為 true，因此它會重複使用目前的 SELECT 陳述式 SelectStatement0。</span><span class="sxs-lookup"><span data-stu-id="63fee-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="63fee-118">輸入新的範圍 (scope1)。</span><span class="sxs-lookup"><span data-stu-id="63fee-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="63fee-119">在瀏覽它的左邊子系 Extent1 之前，另一個 true 會推送到 IsParentAJoin 堆疊上。</span><span class="sxs-lookup"><span data-stu-id="63fee-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>

<span data-ttu-id="63fee-120">當瀏覽 Extent1 時，因為 IsParentAJoin 會傳回 true，所以它會傳回包含 "[dbo].[Products]" 的 SqlBuilder。</span><span class="sxs-lookup"><span data-stu-id="63fee-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="63fee-121">控制權會傳回瀏覽 Join4 的方法。</span><span class="sxs-lookup"><span data-stu-id="63fee-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="63fee-122">將會從 IsParentAJoin 推出項目並呼叫 ProcessJoinInputResul，這樣會將瀏覽 Extent1 的結果附加到 SelectStatement0 的 From 子句。</span><span class="sxs-lookup"><span data-stu-id="63fee-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="63fee-123">建立之輸入繫結名稱 "Extent1" 所適用的新 from 符號 symbol_Extent1 會加入至 SelectStatement0 的 FromExtents，而且 "As" 和 symbol_Extent1 也會附加到 from 子句。</span><span class="sxs-lookup"><span data-stu-id="63fee-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="63fee-124">新的項目會加入至 "Extent1" 的 AllExtentNames，而且值為 0。</span><span class="sxs-lookup"><span data-stu-id="63fee-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="63fee-125">新的項目會加入至符號表中的目前範圍，以便將 "Extent1" 與它的符號 symbol_Extent1 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="63fee-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="63fee-126">Symbol_Extent1 也會加入至 SqlSelectStatement 的 AllJoinExtents。</span><span class="sxs-lookup"><span data-stu-id="63fee-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>

<span data-ttu-id="63fee-127">在瀏覽 Join1 的右邊輸入之前，"LEFT OUTER JOIN" 會加入至 SelectStatement0 的 From 子句。</span><span class="sxs-lookup"><span data-stu-id="63fee-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="63fee-128">因為右邊輸入是 Scan 運算式，所以會再次將 true 推送到 IsParentAJoin 堆疊。</span><span class="sxs-lookup"><span data-stu-id="63fee-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="63fee-129">瀏覽右邊輸入之前的狀態會顯示在下一個圖中。</span><span class="sxs-lookup"><span data-stu-id="63fee-129">The state before visiting the right input as shown in the next figure.</span></span>

<span data-ttu-id="63fee-130">![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="63fee-130">![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>

<span data-ttu-id="63fee-131">右邊輸入會使用與左邊輸入相同的方式來處理。</span><span class="sxs-lookup"><span data-stu-id="63fee-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="63fee-132">瀏覽右邊輸入之後的狀態會顯示在下一個圖中。</span><span class="sxs-lookup"><span data-stu-id="63fee-132">The state after visiting the right input is shown in the next figure.</span></span>

<span data-ttu-id="63fee-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="63fee-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>

<span data-ttu-id="63fee-134">下一個 "false" 會推送到 IsParentAJoin 堆疊上，而且會處理聯結條件 Var(Extent1).CategoryID == Var(Extent2).CategoryID。</span><span class="sxs-lookup"><span data-stu-id="63fee-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="63fee-135">在符號表中查詢之後, \<會將 Var (Extent1) 解析成 symbol_Extent1 >。</span><span class="sxs-lookup"><span data-stu-id="63fee-135">Var(Extent1) is resolved to \<symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="63fee-136">因為處理 Var (Extent1), 所以實例會解析為簡單的符號。[類別], 這\<是具有 symbol1 > 的 SqlBuilder。已傳回「類別 Id」。</span><span class="sxs-lookup"><span data-stu-id="63fee-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="63fee-137">同樣地，將會處理比較的另一端，而且瀏覽聯結條件的結果會附加到 SelectStatement1 的 FROM 子句，並從 IsParentAJoin 堆疊推出 "false" 的值。</span><span class="sxs-lookup"><span data-stu-id="63fee-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>

<span data-ttu-id="63fee-138">這樣就已經完整處理 Join1，而且會從符號表推出範圍。</span><span class="sxs-lookup"><span data-stu-id="63fee-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>

<span data-ttu-id="63fee-139">控制權會傳回正在處理的 Join4，它是 Join1 的父系。</span><span class="sxs-lookup"><span data-stu-id="63fee-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="63fee-140">因為子系重複使用 Select 語句, 所以 Join1 的範圍會以單一聯結符號\<joinSymbol_Join1 > 取代。</span><span class="sxs-lookup"><span data-stu-id="63fee-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol \<joinSymbol_Join1>.</span></span> <span data-ttu-id="63fee-141">此外, 也會將新的專案加入符號表中, 以\<將 Join1 與 joinSymbol_Join1 > 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="63fee-141">Also a new entry is added to the symbol table to associate Join1 with \<joinSymbol_Join1>.</span></span>

<span data-ttu-id="63fee-142">下一個要處理的節點是 Join3，這是 Join4 的第二個子系。</span><span class="sxs-lookup"><span data-stu-id="63fee-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="63fee-143">因為它是右邊子系，所以會將 "false" 推送到 IsParentAJoin 堆疊。</span><span class="sxs-lookup"><span data-stu-id="63fee-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="63fee-144">此時造訪者的狀態會在下一個圖中說明。</span><span class="sxs-lookup"><span data-stu-id="63fee-144">The state of the visitor at this point is illustrated in the next figure.</span></span>

<span data-ttu-id="63fee-145">![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="63fee-145">![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>

<span data-ttu-id="63fee-146">如果是 Join3，IsParentAJoin 會傳回 false 而且需要啟動新的 SqlSelectStatement (SelectStatement1) 並將它推送到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="63fee-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="63fee-147">處理作業會繼續，就像處理之前的聯結一樣，而且新的範圍會推送到堆疊上並處理子系。</span><span class="sxs-lookup"><span data-stu-id="63fee-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="63fee-148">左邊的子系為範圍 (Extent3), 而右邊的子系是聯結 (Join2), 這也需要啟動新的 SqlSelectStatement:SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="63fee-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="63fee-149">Join2 上的子系也是範圍，而且會彙總到 SelectStatement2。</span><span class="sxs-lookup"><span data-stu-id="63fee-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>

<span data-ttu-id="63fee-150">造訪者在瀏覽 Join2 之後，但是完成它的後置處理 (ProcessJoinInputResult) 之前的狀態會顯示在下一個圖中：</span><span class="sxs-lookup"><span data-stu-id="63fee-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>

<span data-ttu-id="63fee-151">![圖表](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="63fee-151">![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>

<span data-ttu-id="63fee-152">在上一個圖中，SelectStatement2 會顯示為自由浮動，因為它已經從堆疊推出但是父系尚未進行後置處理。</span><span class="sxs-lookup"><span data-stu-id="63fee-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="63fee-153">它需要加入至父系的 FROM 部分，但是它沒有 SELECT 子句，所以不是完整 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="63fee-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="63fee-154">所以在此時，預設資料行 (所有資料行都是由它的輸入產生) 會由 AddDefaultColumns 方法加入至 SELECT 清單中。</span><span class="sxs-lookup"><span data-stu-id="63fee-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="63fee-155">AddDefaultColumns 會逐一查看 FromExtents 中的符號，並針對每一個符號加入範圍中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="63fee-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="63fee-156">如果是簡單符號，它會查看符號類型，以便擷取要加入的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="63fee-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="63fee-157">它也會使用資料行名稱填入 AllColumnNames 字典。</span><span class="sxs-lookup"><span data-stu-id="63fee-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="63fee-158">完成的 SelectStatement2 會附加到 SelectStatement1 的 FROM 子句。</span><span class="sxs-lookup"><span data-stu-id="63fee-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>

<span data-ttu-id="63fee-159">接下來，將會建立新的聯結符號來表示 Join2，它會標示為巢狀聯結，並加入至 SelectStatement1 的 AllJoinExtents 和符號表中。</span><span class="sxs-lookup"><span data-stu-id="63fee-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="63fee-160">現在需要處理 Join3 的聯結條件：Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID。</span><span class="sxs-lookup"><span data-stu-id="63fee-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="63fee-161">左邊的處理類似於 Join1 的聯結條件。</span><span class="sxs-lookup"><span data-stu-id="63fee-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="63fee-162">但是，右邊 "Var(Join2).Extent4.OrderID" 的處理則不同，因為需要扁平化聯結。</span><span class="sxs-lookup"><span data-stu-id="63fee-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>

<span data-ttu-id="63fee-163">下一個圖顯示造訪者在處理 DbPropertyExpression "Var(Join2).Extent4.OrderID" 之前的狀態。</span><span class="sxs-lookup"><span data-stu-id="63fee-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>

<span data-ttu-id="63fee-164">考慮如何瀏覽 "Var(Join2).Extent4.OrderID"。</span><span class="sxs-lookup"><span data-stu-id="63fee-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="63fee-165">首先會瀏覽執行個體屬性 "Var(Join2).Extent4" (這是另一個 DbPropertyExpression) 並初次瀏覽它的執行個體 "Var(Join2)"。</span><span class="sxs-lookup"><span data-stu-id="63fee-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="63fee-166">在符號表最上方的範圍中, "Join2" 會解析成\<joinSymbol_join2 >。</span><span class="sxs-lookup"><span data-stu-id="63fee-166">In the top most scope in the symbol table, "Join2" resolves to \<joinSymbol_join2>.</span></span> <span data-ttu-id="63fee-167">在 DbPropertyExpression 處理 "Var(Join2).Extent4" 的瀏覽方法中，請注意當瀏覽執行個體時已傳回聯結符號，而且需要扁平化。</span><span class="sxs-lookup"><span data-stu-id="63fee-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>

<span data-ttu-id="63fee-168">因為它是一個嵌套聯結, 所以我們會在聯結符號的 NameToExtent 字典中查閱屬性 ".extent4.orderid", 將它解析為\<symbol_Extent4 > 並傳回新的 SymbolPair (\<joinSymbol_join2 >, \<symbol_Extent4>)。</span><span class="sxs-lookup"><span data-stu-id="63fee-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to \<symbol_Extent4> and return a new SymbolPair(\<joinSymbol_join2>, \<symbol_Extent4>).</span></span> <span data-ttu-id="63fee-169">因為符號組是從 "Var (Join2)" 的實例處理傳回的.Extent4.orderid 會從該符號配對的 ColumnPart (\<symbol_Extent4 >) 解析屬性 "「訂單」, 其中包含它所代表之範圍的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="63fee-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (\<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="63fee-170">因此, "Var (Join2).Extent4.orderid 會解析為 { \<joinSymbol_Join2 >, ".", \<symbol_OrderID >}。</span><span class="sxs-lookup"><span data-stu-id="63fee-170">So, "Var(Join2).Extent4.OrderID" is resolved to { \<joinSymbol_Join2>, ".", \<symbol_OrderID>}.</span></span>

<span data-ttu-id="63fee-171">Join4 的聯結條件會以類似的方式處理。</span><span class="sxs-lookup"><span data-stu-id="63fee-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="63fee-172">控制權會傳回已處理最上層專案的 VisitInputExpression 方法。</span><span class="sxs-lookup"><span data-stu-id="63fee-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="63fee-173">在查看傳回之 SelectStatement0 的 FromExtents 時，輸入會識別為聯結，而且會移除原始範圍，並使用只有聯結符號的新範圍來加以取代。</span><span class="sxs-lookup"><span data-stu-id="63fee-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="63fee-174">也會更新符號表，接下來會處理專案的投射部分。</span><span class="sxs-lookup"><span data-stu-id="63fee-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="63fee-175">屬性的解析以及聯結範圍的扁平化如同之前所述。</span><span class="sxs-lookup"><span data-stu-id="63fee-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>

<span data-ttu-id="63fee-176">![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="63fee-176">![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>

<span data-ttu-id="63fee-177">最後會產生下列 SqlSelectStatement：</span><span class="sxs-lookup"><span data-stu-id="63fee-177">Finally, the following SqlSelectStatement is produced:</span></span>

```
SELECT:
  "1", " AS ", "[C1]",
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",
        "INNER JOIN ",
        " (", SELECT:
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,
<joinSymbol_Join2>, ".", <symbol_ExciseTax>
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,
"LEFT OUTER JOIN ",
" (", SELECT:
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>
```

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="63fee-178">SQL 產生的第二個階段:產生字串命令</span><span class="sxs-lookup"><span data-stu-id="63fee-178">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="63fee-179">第二個階段會產生實際的符號名稱，我們只著重於代表 "OrderID" 資料行的符號，因為這個情況下需要解決衝突。</span><span class="sxs-lookup"><span data-stu-id="63fee-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="63fee-180">這些會在 SqlSelectStatement 中強調。</span><span class="sxs-lookup"><span data-stu-id="63fee-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="63fee-181">請注意，圖中所用的尾碼只是為了強調這些是不同的執行個體，不是為了代表任何新的名稱，因為在這個階段尚未指派其最終的名稱 (可能與原始名稱不同)。</span><span class="sxs-lookup"><span data-stu-id="63fee-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>

<span data-ttu-id="63fee-182">找到需要重新命名的第一個符號是\<symbol_OrderID >。</span><span class="sxs-lookup"><span data-stu-id="63fee-182">The first symbol found that needs to be renamed is \<symbol_OrderID>.</span></span> <span data-ttu-id="63fee-183">它的新名稱會指派為 "OrderID1"，而且 1 會標示為上次用於 "OrderID" 的尾碼，而且此符號會標示為不需要重新命名。</span><span class="sxs-lookup"><span data-stu-id="63fee-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="63fee-184">接下來, 會找到\<symbol_OrderID_2 > 的第一個使用方式。</span><span class="sxs-lookup"><span data-stu-id="63fee-184">Next, the first usage of \<symbol_OrderID_2> is found.</span></span> <span data-ttu-id="63fee-185">它會重新命名來使用下一個可用的尾碼 ("OrderID2") 而且會再次標示為不需要重新命名，所以下次使用它時就不會重新命名。</span><span class="sxs-lookup"><span data-stu-id="63fee-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="63fee-186">這也適用于\<symbol_OrderID_3 >。</span><span class="sxs-lookup"><span data-stu-id="63fee-186">This is done for \<symbol_OrderID_3> too.</span></span>

<span data-ttu-id="63fee-187">第二個階段結束時，將會產生最終的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="63fee-187">At the end of the second phase, the final SQL statement is generated.</span></span>

## <a name="see-also"></a><span data-ttu-id="63fee-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63fee-188">See also</span></span>

- [<span data-ttu-id="63fee-189">範例提供者中的 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="63fee-189">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
