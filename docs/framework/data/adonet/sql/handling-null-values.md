---
title: 處理 Null 值
description: 瞭解 SQL Server 的 .NET Framework Data Provider 如何處理 null、如何讀取 null 和 SqlBoolean、三值邏輯，以及指派 null 值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2dda65f605ea9de616f01d6e52eb4e0e5def4db7
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982514"
---
# <a name="handling-null-values"></a><span data-ttu-id="bddc5-103">處理 Null 值</span><span class="sxs-lookup"><span data-stu-id="bddc5-103">Handling Null Values</span></span>

<span data-ttu-id="bddc5-104">在關聯式資料庫中，當資料行中的值為未知或遺漏時，就會使用 Null 值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-104">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="bddc5-105">Null 不是空字串 (針對字元或日期時間資料類型)，也不是零值 (針對數值資料類型)。</span><span class="sxs-lookup"><span data-stu-id="bddc5-105">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="bddc5-106">ANSI SQL-92 規格指出，所有資料類型的 Null 都必須相同，因此，所有 Null 都會以一致的方式來處理。</span><span class="sxs-lookup"><span data-stu-id="bddc5-106">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="bddc5-107"><xref:System.Data.SqlTypes> 命名空間會藉由實作 <xref:System.Data.SqlTypes.INullable> 介面來提供 Null 語意。</span><span class="sxs-lookup"><span data-stu-id="bddc5-107">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="bddc5-108"><xref:System.Data.SqlTypes> 中的每個資料類型都有自己的 `IsNull` 屬性，以及可指派給該資料類型之執行個體的 `Null` 值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-108">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bddc5-109">.NET Framework 2.0 版引進了可為 null 的實值型別支援，可讓程式設計人員擴充實值型別，以代表基礎型別的所有值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-109">The .NET Framework version 2.0 introduced support for nullable value types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="bddc5-110">這些 CLR 可為 null 實數值型別代表結構的實例 <xref:System.Nullable> 。</span><span class="sxs-lookup"><span data-stu-id="bddc5-110">These CLR nullable value types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="bddc5-111">已將數值類型 Boxed 和 Unboxed 時，此功能特別有用，可提供與物件類型的增強相容性。</span><span class="sxs-lookup"><span data-stu-id="bddc5-111">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="bddc5-112">CLR 可為 null 的實值型別不適合儲存資料庫 null，因為 ANSI SQL null 的行為與 `null` 參考 (或 Visual Basic) 的行為相同 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="bddc5-112">CLR nullable value types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="bddc5-113">若要使用資料庫 ANSI SQL Null 值，請使用 <xref:System.Data.SqlTypes> Null，而不是 <xref:System.Nullable>。</span><span class="sxs-lookup"><span data-stu-id="bddc5-113">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="bddc5-114">如需在 Visual Basic 中使用 CLR 值 nullable 型別的詳細資訊，請參閱[可為](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)null 的實值型別，而針對 c #，請參閱[可為 null](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="bddc5-114">For more information on working with CLR value nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="bddc5-115">Null 及三種值的邏輯</span><span class="sxs-lookup"><span data-stu-id="bddc5-115">Nulls and Three-Valued Logic</span></span>  

 <span data-ttu-id="bddc5-116">在資料行定義中允許 Null 值，會在您的應用程式中引進三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="bddc5-116">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="bddc5-117">比較可以評估為三個條件的其中一個：</span><span class="sxs-lookup"><span data-stu-id="bddc5-117">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="bddc5-118">True</span><span class="sxs-lookup"><span data-stu-id="bddc5-118">True</span></span>  
  
- <span data-ttu-id="bddc5-119">False</span><span class="sxs-lookup"><span data-stu-id="bddc5-119">False</span></span>  
  
- <span data-ttu-id="bddc5-120">Unknown</span><span class="sxs-lookup"><span data-stu-id="bddc5-120">Unknown</span></span>  
  
 <span data-ttu-id="bddc5-121">因為 Null 會被視為未知，所以不會將彼此相比較的兩個 Null 值視為相等。</span><span class="sxs-lookup"><span data-stu-id="bddc5-121">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="bddc5-122">在使用算術運算子的運算式中，如果有任何運算元是 Null，結果也會是 Null。</span><span class="sxs-lookup"><span data-stu-id="bddc5-122">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="bddc5-123">Null 和 SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="bddc5-123">Nulls and SqlBoolean</span></span>  

 <span data-ttu-id="bddc5-124">任何 <xref:System.Data.SqlTypes> 間的比較都將傳回 <xref:System.Data.SqlTypes.SqlBoolean>。</span><span class="sxs-lookup"><span data-stu-id="bddc5-124">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="bddc5-125">每個 `IsNull` 的 `SqlType` 函數都會傳回 <xref:System.Data.SqlTypes.SqlBoolean>，而且可用來檢查 Null 值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-125">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="bddc5-126">下列事實資料表示範 AND、OR 及 NOT 運算子如何在出現 Null 值的情況下運作</span><span class="sxs-lookup"><span data-stu-id="bddc5-126">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="bddc5-127">(T=true、F=false 及 U=unknown，或 Null)。</span><span class="sxs-lookup"><span data-stu-id="bddc5-127">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="bddc5-128">![事實資料表](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="bddc5-128">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="bddc5-129">瞭解 ANSI_NULLS 選項</span><span class="sxs-lookup"><span data-stu-id="bddc5-129">Understanding the ANSI_NULLS Option</span></span>  

 <span data-ttu-id="bddc5-130"><xref:System.Data.SqlTypes> 提供的語意與在 SQL Server 中設定 ANSI_NULLS 選項時相同。</span><span class="sxs-lookup"><span data-stu-id="bddc5-130"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="bddc5-131">\* \| 如果有任何運算元或引數為 null （屬性除外），則所有算術運算子 (+、-、、/、% ) 、位運算子 (~、&、) 和大部分函數都會傳回 null `IsNull` 。</span><span class="sxs-lookup"><span data-stu-id="bddc5-131">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="bddc5-132">ANSI SQL-92 標準不支援 WHERE 子句中的 *columnName* = NULL。</span><span class="sxs-lookup"><span data-stu-id="bddc5-132">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="bddc5-133">在 SQL Server 中，ANSI_NULLS 選項會控制資料庫中預設的可 NULL 性，以及對 Null 值的比較評估。</span><span class="sxs-lookup"><span data-stu-id="bddc5-133">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="bddc5-134">如果 ANSI_NULLS 已開啟 (預設值)，則在測試 Null 值時，必須在運算式中使用 IS NULL 運算子。</span><span class="sxs-lookup"><span data-stu-id="bddc5-134">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="bddc5-135">例如，當 ANSI_NULLS 是 ON 時，下列比較永遠都會產生未知：</span><span class="sxs-lookup"><span data-stu-id="bddc5-135">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="bddc5-136">與包含 Null 值的變數進行比較也會產生未知：</span><span class="sxs-lookup"><span data-stu-id="bddc5-136">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="bddc5-137">使用 IS NULL 或 IS NOT NULL 述詞可以測試是否為 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-137">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="bddc5-138">不過這樣會增加 WHERE 子句的複雜度。</span><span class="sxs-lookup"><span data-stu-id="bddc5-138">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="bddc5-139">例如，AdventureWorks Customer 資料表中的 TerritoryID 資料行允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-139">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="bddc5-140">如果 SELECT 陳述式要測試其他資料行是否有 Null 值，必須包含 IS NULL 述詞：</span><span class="sxs-lookup"><span data-stu-id="bddc5-140">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="bddc5-141">如果您將 SQL Server 中的 ANSI_NULLS 設定為 off，則可建立使用等號比較運算子來比較 Null 的運算式。</span><span class="sxs-lookup"><span data-stu-id="bddc5-141">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="bddc5-142">不過，您無法防止不同的連線來為該連線設定 Null 選項。</span><span class="sxs-lookup"><span data-stu-id="bddc5-142">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="bddc5-143">不論連線的 ANSI_NULLS 設定為何，使用 IS NULL 來測試 Null 值一律可行。</span><span class="sxs-lookup"><span data-stu-id="bddc5-143">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="bddc5-144">`DataSet` 中不支援將 ANSI_NULLS 設定為 off，其始終會遵循 ANSI SQL-92 標準來處理 <xref:System.Data.SqlTypes> 中的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-144">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="bddc5-145">指派 Null 值</span><span class="sxs-lookup"><span data-stu-id="bddc5-145">Assigning Null Values</span></span>  

 <span data-ttu-id="bddc5-146">Null 值是特殊的，它們的儲存和指派語意在不同類型系統和儲存系統之間各不相同。</span><span class="sxs-lookup"><span data-stu-id="bddc5-146">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="bddc5-147">`Dataset` 是設計來搭配不同的類型和儲存系統使用。</span><span class="sxs-lookup"><span data-stu-id="bddc5-147">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="bddc5-148">此節描述在不同類型系統間的 <xref:System.Data.DataColumn> 中，將 Null 值指派給 <xref:System.Data.DataRow> 的 Null 語意。</span><span class="sxs-lookup"><span data-stu-id="bddc5-148">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="bddc5-149">此指派適用於任何類型的 `DataColumn`。</span><span class="sxs-lookup"><span data-stu-id="bddc5-149">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="bddc5-150">如果類型實作 `INullable`，就會將 `DBNull.Value` 強制轉型為適當的強型別 Null 值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-150">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="bddc5-151">所有 <xref:System.Data.SqlTypes> 資料類型都會實作 `INullable`。</span><span class="sxs-lookup"><span data-stu-id="bddc5-151">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="bddc5-152">如果強型別 Null 值可以使用隱含轉換運算子轉換為資料行的資料類型，則指派應可順利完成。</span><span class="sxs-lookup"><span data-stu-id="bddc5-152">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="bddc5-153">否則會擲回轉換無效的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bddc5-153">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="bddc5-154">如果 'null' 是指定 `DataColumn` 資料類型的合法值，就會強制轉型為適當的 `DbNull.Value` 或與 `Null` 類型 (`INullable`) 相關聯的 `SqlType.Null`。</span><span class="sxs-lookup"><span data-stu-id="bddc5-154">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="bddc5-155">如果是 UDT 資料行，一律會根據與 `DataColumn` 相關聯的類型來儲存 Null。</span><span class="sxs-lookup"><span data-stu-id="bddc5-155">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="bddc5-156">請考慮與 `DataColumn` 相關聯的 UDT 案例，其不會實作 `INullable`，但其子類別會。</span><span class="sxs-lookup"><span data-stu-id="bddc5-156">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="bddc5-157">在此案例中，如果已指派與衍生類別相關聯的強型別 Null 值，它就會儲存為不具類型的 `DbNull.Value`，因為 Null 儲存一律會與 DataColumn 的資料類型一致。</span><span class="sxs-lookup"><span data-stu-id="bddc5-157">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bddc5-158">`Nullable<T>` 中目前不支援 <xref:System.Nullable> 或 `DataSet` 結構。</span><span class="sxs-lookup"><span data-stu-id="bddc5-158">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="bddc5-159">多個資料行 (資料列) 指派</span><span class="sxs-lookup"><span data-stu-id="bddc5-159">Multiple Column (Row) Assignment</span></span>  

 <span data-ttu-id="bddc5-160">`DataTable.Add`、`DataTable.LoadDataRow` 或其他接受對應到資料列之 <xref:System.Data.DataRow.ItemArray%2A> 的 API，會將 'null' 對應到 DataColumn 的預設值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-160">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="bddc5-161">如果陣列中的物件包含 `DbNull.Value` 或其強型別的對應項，即會套用前述的相同規則。</span><span class="sxs-lookup"><span data-stu-id="bddc5-161">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="bddc5-162">此外，下列規則適用於 `DataRow.["columnName"]` Null 指派的執行個體：</span><span class="sxs-lookup"><span data-stu-id="bddc5-162">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="bddc5-163">除了 *default* 強型別 `DbNull.Value` null 資料行是適當的強型別 null 值之外，所有的預設值都是。</span><span class="sxs-lookup"><span data-stu-id="bddc5-163">The *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="bddc5-164">絕對不會在序列化到 XML 檔案期間寫出 Null 值 (就像 "xsi:nil")。</span><span class="sxs-lookup"><span data-stu-id="bddc5-164">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="bddc5-165">序列化到 XML 時，一律會寫出所有非 Null 值 (包括預設值)。</span><span class="sxs-lookup"><span data-stu-id="bddc5-165">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="bddc5-166">這不同於 XSD/XML 語意，其中 Null 值 (xsi:nil) 是明確的，而預設值是隱含的 (如果未出現在 XML 中，驗證剖析器就能夠從相關聯的 XSD 結構描述中取得它)。</span><span class="sxs-lookup"><span data-stu-id="bddc5-166">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="bddc5-167">如果是 `DataTable`，則情況恰恰相反：Null 值是隱含的，而預設值是明確的。</span><span class="sxs-lookup"><span data-stu-id="bddc5-167">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="bddc5-168">從 XML 輸入讀取之資料列的所有遺漏資料行值都會指派為 Null。</span><span class="sxs-lookup"><span data-stu-id="bddc5-168">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="bddc5-169">使用 <xref:System.Data.DataTable.NewRow%2A> 或類似方法建立的資料列都會被指派 DataColumn 的預設值。</span><span class="sxs-lookup"><span data-stu-id="bddc5-169">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="bddc5-170"><xref:System.Data.DataRow.IsNull%2A> 方法會針對 `true` 和 `DbNull.Value` 傳回 `INullable.Null`。</span><span class="sxs-lookup"><span data-stu-id="bddc5-170">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="bddc5-171">指派 Null 值</span><span class="sxs-lookup"><span data-stu-id="bddc5-171">Assigning Null Values</span></span>  

 <span data-ttu-id="bddc5-172">所有 <xref:System.Data.SqlTypes> 執行個體的預設值均為 Null。</span><span class="sxs-lookup"><span data-stu-id="bddc5-172">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="bddc5-173"><xref:System.Data.SqlTypes> 中的 Null 是類型專屬的，無法以單一值表示，例如 `DbNull`。</span><span class="sxs-lookup"><span data-stu-id="bddc5-173">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="bddc5-174">使用 `IsNull` 屬性來檢查 Null。</span><span class="sxs-lookup"><span data-stu-id="bddc5-174">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="bddc5-175">Null 值可以指派給 <xref:System.Data.DataColumn>，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="bddc5-175">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="bddc5-176">您可以直接將 Null 值指派給 `SqlTypes` 變數，而不會觸發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bddc5-176">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="bddc5-177">範例</span><span class="sxs-lookup"><span data-stu-id="bddc5-177">Example</span></span>  

 <span data-ttu-id="bddc5-178">下列程式碼範例會建立 <xref:System.Data.DataTable>，其中包含兩個定義為 <xref:System.Data.SqlTypes.SqlInt32> 和 <xref:System.Data.SqlTypes.SqlString> 的資料行。</span><span class="sxs-lookup"><span data-stu-id="bddc5-178">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="bddc5-179">程式碼會新增一個已知值的資料列、一個 Null 值的資料列，然後逐一查看 <xref:System.Data.DataTable>，將值指派給變數，並在主控台視窗中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="bddc5-179">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="bddc5-180">此範例會顯示下列結果：</span><span class="sxs-lookup"><span data-stu-id="bddc5-180">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="bddc5-181">將 Null 值與 SqlType 及 CLR 型別進行比較</span><span class="sxs-lookup"><span data-stu-id="bddc5-181">Comparing Null Values with SqlTypes and CLR Types</span></span>  

 <span data-ttu-id="bddc5-182">比較 Null 值時，請務必了解 `Equals` 方法在 <xref:System.Data.SqlTypes> 中評估 Null 值之方式間的差異 (相較於其使用 CLR 類型的方式)。</span><span class="sxs-lookup"><span data-stu-id="bddc5-182">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="bddc5-183">所有 <xref:System.Data.SqlTypes>`Equals` 方法都會使用資料庫語意來評估 Null 值：如果其中一個或兩個值都是 Null，則比較會產生 Null。</span><span class="sxs-lookup"><span data-stu-id="bddc5-183">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="bddc5-184">另一方面，在兩個 `Equals` 上使用 CLR <xref:System.Data.SqlTypes> 方法，將會在兩者均為 Null 時產生 True。</span><span class="sxs-lookup"><span data-stu-id="bddc5-184">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="bddc5-185">這會反映使用執行個體方法 (例如 CLR `String.Equals` 方法) 和使用靜態/共用方法 (`SqlString.Equals`) 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="bddc5-185">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="bddc5-186">下列範例示範在 `SqlString.Equals` 方法與 `String.Equals` 方法之間，分別傳遞一對 Null 值，然後傳遞一對空字串時的結果差異。</span><span class="sxs-lookup"><span data-stu-id="bddc5-186">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="bddc5-187">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bddc5-187">The code produces the following output:</span></span>  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a><span data-ttu-id="bddc5-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bddc5-188">See also</span></span>

- [<span data-ttu-id="bddc5-189">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bddc5-189">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- <span data-ttu-id="bddc5-190">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="bddc5-190">[ADO.NET Overview](../ado-net-overview.md)</span></span>
