---
title: 處理 Null 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: c64f11c00174981925342f1493ef0b809a57ecb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148643"
---
# <a name="handling-null-values"></a><span data-ttu-id="32b59-102">處理 Null 值</span><span class="sxs-lookup"><span data-stu-id="32b59-102">Handling Null Values</span></span>
<span data-ttu-id="32b59-103">在關聯式資料庫中，當資料行中的值為未知或遺漏時，就會使用 Null 值。</span><span class="sxs-lookup"><span data-stu-id="32b59-103">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="32b59-104">Null 不是空字串 (針對字元或日期時間資料類型)，也不是零值 (針對數值資料類型)。</span><span class="sxs-lookup"><span data-stu-id="32b59-104">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="32b59-105">ANSI SQL-92 規格指出，所有資料類型的 Null 都必須相同，因此，所有 Null 都會以一致的方式來處理。</span><span class="sxs-lookup"><span data-stu-id="32b59-105">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="32b59-106"><xref:System.Data.SqlTypes> 命名空間會藉由實作 <xref:System.Data.SqlTypes.INullable> 介面來提供 Null 語意。</span><span class="sxs-lookup"><span data-stu-id="32b59-106">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="32b59-107"><xref:System.Data.SqlTypes> 中的每個資料類型都有自己的 `IsNull` 屬性，以及可指派給該資料類型之執行個體的 `Null` 值。</span><span class="sxs-lookup"><span data-stu-id="32b59-107">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32b59-108">.NET Framework 2.0 版開始支援可為 Null 型別，這讓程式設計人員得以擴充實值型別，以表示基礎型別所有的值。</span><span class="sxs-lookup"><span data-stu-id="32b59-108">The .NET Framework version 2.0 introduced support for nullable types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="32b59-109">這些可為 Null 的 CLR 類型代表 <xref:System.Nullable> 結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="32b59-109">These CLR nullable types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="32b59-110">已將數值類型 Boxed 和 Unboxed 時，此功能特別有用，可提供與物件類型的增強相容性。</span><span class="sxs-lookup"><span data-stu-id="32b59-110">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="32b59-111">可為 Null 的 CLR 類型不適合用來儲存資料庫 Null，因為 ANSI SQL Null 的行為與 `null` 參考 (或 Visual Basic 中的 `Nothing`) 的運作方式不同。</span><span class="sxs-lookup"><span data-stu-id="32b59-111">CLR nullable types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="32b59-112">若要使用資料庫 ANSI SQL Null 值，請使用 <xref:System.Data.SqlTypes> Null，而不是 <xref:System.Nullable>。</span><span class="sxs-lookup"><span data-stu-id="32b59-112">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="32b59-113">有關在視覺化基本版中使用 CLR 可空類型的詳細資訊，請參閱[空數值型別](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)，有關 C#，請參閱[空數值型別](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="32b59-113">For more information on working with CLR nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="32b59-114">Null 及三種值的邏輯</span><span class="sxs-lookup"><span data-stu-id="32b59-114">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="32b59-115">在資料行定義中允許 Null 值，會在您的應用程式中引進三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="32b59-115">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="32b59-116">比較可以評估為三個條件的其中一個：</span><span class="sxs-lookup"><span data-stu-id="32b59-116">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="32b59-117">True</span><span class="sxs-lookup"><span data-stu-id="32b59-117">True</span></span>  
  
- <span data-ttu-id="32b59-118">False</span><span class="sxs-lookup"><span data-stu-id="32b59-118">False</span></span>  
  
- <span data-ttu-id="32b59-119">Unknown</span><span class="sxs-lookup"><span data-stu-id="32b59-119">Unknown</span></span>  
  
 <span data-ttu-id="32b59-120">因為 Null 會被視為未知，所以不會將彼此相比較的兩個 Null 值視為相等。</span><span class="sxs-lookup"><span data-stu-id="32b59-120">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="32b59-121">在使用算術運算子的運算式中，如果有任何運算元是 Null，結果也會是 Null。</span><span class="sxs-lookup"><span data-stu-id="32b59-121">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="32b59-122">Null 和 SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="32b59-122">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="32b59-123">任何 <xref:System.Data.SqlTypes> 間的比較都將傳回 <xref:System.Data.SqlTypes.SqlBoolean>。</span><span class="sxs-lookup"><span data-stu-id="32b59-123">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="32b59-124">每個 `SqlType` 的 `IsNull` 函數都會傳回 <xref:System.Data.SqlTypes.SqlBoolean>，而且可用來檢查 Null 值。</span><span class="sxs-lookup"><span data-stu-id="32b59-124">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="32b59-125">下列事實資料表示範 AND、OR 及 NOT 運算子如何在出現 Null 值的情況下運作</span><span class="sxs-lookup"><span data-stu-id="32b59-125">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="32b59-126">(T=true、F=false 及 U=unknown，或 Null)。</span><span class="sxs-lookup"><span data-stu-id="32b59-126">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="32b59-127">![事實資料表](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="32b59-127">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="32b59-128">瞭解 ANSI_NULLS 選項</span><span class="sxs-lookup"><span data-stu-id="32b59-128">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="32b59-129"><xref:System.Data.SqlTypes> 提供的語意與在 SQL Server 中設定 ANSI_NULLS 選項時相同。</span><span class="sxs-lookup"><span data-stu-id="32b59-129"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="32b59-130">如果任一運算元或參數為\*空，則所有算術運算子 （*、-、/、%）位運算子（*、&）\|和大多數函數都返回 null，但屬性`IsNull`除外。</span><span class="sxs-lookup"><span data-stu-id="32b59-130">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="32b59-131">ANSI SQL-92 標準不支援 WHERE 子句中的 *columnName* = NULL。</span><span class="sxs-lookup"><span data-stu-id="32b59-131">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="32b59-132">在 SQL Server 中，ANSI_NULLS 選項會控制資料庫中預設的可 NULL 性，以及對 Null 值的比較評估。</span><span class="sxs-lookup"><span data-stu-id="32b59-132">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="32b59-133">如果 ANSI_NULLS 已開啟 (預設值)，則在測試 Null 值時，必須在運算式中使用 IS NULL 運算子。</span><span class="sxs-lookup"><span data-stu-id="32b59-133">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="32b59-134">例如，當 ANSI_NULLS 是 ON 時，下列比較永遠都會產生未知：</span><span class="sxs-lookup"><span data-stu-id="32b59-134">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="32b59-135">與包含 Null 值的變數進行比較也會產生未知：</span><span class="sxs-lookup"><span data-stu-id="32b59-135">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="32b59-136">使用 IS NULL 或 IS NOT NULL 述詞可以測試是否為 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="32b59-136">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="32b59-137">不過這樣會增加 WHERE 子句的複雜度。</span><span class="sxs-lookup"><span data-stu-id="32b59-137">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="32b59-138">例如，AdventureWorks Customer 資料表中的 TerritoryID 資料行允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="32b59-138">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="32b59-139">如果 SELECT 陳述式要測試其他資料行是否有 Null 值，必須包含 IS NULL 述詞：</span><span class="sxs-lookup"><span data-stu-id="32b59-139">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="32b59-140">如果您將 SQL Server 中的 ANSI_NULLS 設定為 off，則可建立使用等號比較運算子來比較 Null 的運算式。</span><span class="sxs-lookup"><span data-stu-id="32b59-140">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="32b59-141">不過，您無法防止不同的連線來為該連線設定 Null 選項。</span><span class="sxs-lookup"><span data-stu-id="32b59-141">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="32b59-142">不論連線的 ANSI_NULLS 設定為何，使用 IS NULL 來測試 Null 值一律可行。</span><span class="sxs-lookup"><span data-stu-id="32b59-142">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="32b59-143">`DataSet` 中不支援將 ANSI_NULLS 設定為 off，其始終會遵循 ANSI SQL-92 標準來處理 <xref:System.Data.SqlTypes> 中的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="32b59-143">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="32b59-144">指派 Null 值</span><span class="sxs-lookup"><span data-stu-id="32b59-144">Assigning Null Values</span></span>  
 <span data-ttu-id="32b59-145">Null 值是特殊的，它們的儲存和指派語意在不同類型系統和儲存系統之間各不相同。</span><span class="sxs-lookup"><span data-stu-id="32b59-145">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="32b59-146">`Dataset` 是設計來搭配不同的類型和儲存系統使用。</span><span class="sxs-lookup"><span data-stu-id="32b59-146">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="32b59-147">此節描述在不同類型系統間的 <xref:System.Data.DataRow> 中，將 Null 值指派給 <xref:System.Data.DataColumn> 的 Null 語意。</span><span class="sxs-lookup"><span data-stu-id="32b59-147">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="32b59-148">此指派適用於任何類型的 `DataColumn`。</span><span class="sxs-lookup"><span data-stu-id="32b59-148">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="32b59-149">如果類型實作 `INullable`，就會將 `DBNull.Value` 強制轉型為適當的強型別 Null 值。</span><span class="sxs-lookup"><span data-stu-id="32b59-149">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="32b59-150">所有 <xref:System.Data.SqlTypes> 資料類型都會實作 `INullable`。</span><span class="sxs-lookup"><span data-stu-id="32b59-150">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="32b59-151">如果強型別 Null 值可以使用隱含轉換運算子轉換為資料行的資料類型，則指派應可順利完成。</span><span class="sxs-lookup"><span data-stu-id="32b59-151">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="32b59-152">否則會擲回轉換無效的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="32b59-152">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="32b59-153">如果 'null' 是指定 `DataColumn` 資料類型的合法值，就會強制轉型為適當的 `DbNull.Value` 或與 `INullable` 類型 (`SqlType.Null`) 相關聯的 `Null`。</span><span class="sxs-lookup"><span data-stu-id="32b59-153">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="32b59-154">如果是 UDT 資料行，一律會根據與 `DataColumn` 相關聯的類型來儲存 Null。</span><span class="sxs-lookup"><span data-stu-id="32b59-154">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="32b59-155">請考慮與 `DataColumn` 相關聯的 UDT 案例，其不會實作 `INullable`，但其子類別會。</span><span class="sxs-lookup"><span data-stu-id="32b59-155">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="32b59-156">在此案例中，如果已指派與衍生類別相關聯的強型別 Null 值，它就會儲存為不具類型的 `DbNull.Value`，因為 Null 儲存一律會與 DataColumn 的資料類型一致。</span><span class="sxs-lookup"><span data-stu-id="32b59-156">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32b59-157">`DataSet` 中目前不支援 `Nullable<T>` 或 <xref:System.Nullable> 結構。</span><span class="sxs-lookup"><span data-stu-id="32b59-157">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="32b59-158">多個資料行 (資料列) 指派</span><span class="sxs-lookup"><span data-stu-id="32b59-158">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="32b59-159">`DataTable.Add`、`DataTable.LoadDataRow` 或其他接受對應到資料列之 <xref:System.Data.DataRow.ItemArray%2A> 的 API，會將 'null' 對應到 DataColumn 的預設值。</span><span class="sxs-lookup"><span data-stu-id="32b59-159">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="32b59-160">如果陣列中的物件包含 `DbNull.Value` 或其強型別的對應項，即會套用前述的相同規則。</span><span class="sxs-lookup"><span data-stu-id="32b59-160">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="32b59-161">此外，下列規則適用於 `DataRow.["columnName"]` Null 指派的執行個體：</span><span class="sxs-lookup"><span data-stu-id="32b59-161">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="32b59-162">除了強型別 Null 資料行具有適當的強型別 Null 值之外，所有其他項目的預設 *default* 值都為 `DbNull.Value`。</span><span class="sxs-lookup"><span data-stu-id="32b59-162">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="32b59-163">絕對不會在序列化到 XML 檔案期間寫出 Null 值 (就像 "xsi:nil")。</span><span class="sxs-lookup"><span data-stu-id="32b59-163">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="32b59-164">序列化到 XML 時，一律會寫出所有非 Null 值 (包括預設值)。</span><span class="sxs-lookup"><span data-stu-id="32b59-164">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="32b59-165">這不同於 XSD/XML 語意，其中 Null 值 (xsi:nil) 是明確的，而預設值是隱含的 (如果未出現在 XML 中，驗證剖析器就能夠從相關聯的 XSD 結構描述中取得它)。</span><span class="sxs-lookup"><span data-stu-id="32b59-165">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="32b59-166">如果是 `DataTable`，則情況恰恰相反：Null 值是隱含的，而預設值是明確的。</span><span class="sxs-lookup"><span data-stu-id="32b59-166">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="32b59-167">從 XML 輸入讀取之資料列的所有遺漏資料行值都會指派為 Null。</span><span class="sxs-lookup"><span data-stu-id="32b59-167">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="32b59-168">使用 <xref:System.Data.DataTable.NewRow%2A> 或類似方法建立的資料列都會被指派 DataColumn 的預設值。</span><span class="sxs-lookup"><span data-stu-id="32b59-168">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="32b59-169"><xref:System.Data.DataRow.IsNull%2A> 方法會針對 `DbNull.Value` 和 `INullable.Null` 傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="32b59-169">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="32b59-170">指派 Null 值</span><span class="sxs-lookup"><span data-stu-id="32b59-170">Assigning Null Values</span></span>  
 <span data-ttu-id="32b59-171">所有 <xref:System.Data.SqlTypes> 執行個體的預設值均為 Null。</span><span class="sxs-lookup"><span data-stu-id="32b59-171">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="32b59-172"><xref:System.Data.SqlTypes> 中的 Null 是類型專屬的，無法以單一值表示，例如 `DbNull`。</span><span class="sxs-lookup"><span data-stu-id="32b59-172">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="32b59-173">使用 `IsNull` 屬性來檢查 Null。</span><span class="sxs-lookup"><span data-stu-id="32b59-173">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="32b59-174">Null 值可以指派給 <xref:System.Data.DataColumn>，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="32b59-174">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="32b59-175">您可以直接將 Null 值指派給 `SqlTypes` 變數，而不會觸發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="32b59-175">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="32b59-176">範例</span><span class="sxs-lookup"><span data-stu-id="32b59-176">Example</span></span>  
 <span data-ttu-id="32b59-177">下列程式碼範例會建立 <xref:System.Data.DataTable>，其中包含兩個定義為 <xref:System.Data.SqlTypes.SqlInt32> 和 <xref:System.Data.SqlTypes.SqlString> 的資料行。</span><span class="sxs-lookup"><span data-stu-id="32b59-177">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="32b59-178">程式碼會新增一個已知值的資料列、一個 Null 值的資料列，然後逐一查看 <xref:System.Data.DataTable>，將值指派給變數，並在主控台視窗中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="32b59-178">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="32b59-179">此範例會顯示下列結果：</span><span class="sxs-lookup"><span data-stu-id="32b59-179">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="32b59-180">將 Null 值與 SqlType 及 CLR 型別進行比較</span><span class="sxs-lookup"><span data-stu-id="32b59-180">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="32b59-181">比較 Null 值時，請務必了解 `Equals` 方法在 <xref:System.Data.SqlTypes> 中評估 Null 值之方式間的差異 (相較於其使用 CLR 類型的方式)。</span><span class="sxs-lookup"><span data-stu-id="32b59-181">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="32b59-182">所有 <xref:System.Data.SqlTypes>`Equals` 方法都會使用資料庫語意來評估 Null 值：如果其中一個或兩個值都是 Null，則比較會產生 Null。</span><span class="sxs-lookup"><span data-stu-id="32b59-182">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="32b59-183">另一方面，在兩個 <xref:System.Data.SqlTypes> 上使用 CLR `Equals` 方法，將會在兩者均為 Null 時產生 True。</span><span class="sxs-lookup"><span data-stu-id="32b59-183">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="32b59-184">這會反映使用執行個體方法 (例如 CLR `String.Equals` 方法) 和使用靜態/共用方法 (`SqlString.Equals`) 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="32b59-184">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="32b59-185">下列範例示範在 `SqlString.Equals` 方法與 `String.Equals` 方法之間，分別傳遞一對 Null 值，然後傳遞一對空字串時的結果差異。</span><span class="sxs-lookup"><span data-stu-id="32b59-185">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="32b59-186">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="32b59-186">The code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32b59-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32b59-187">See also</span></span>

- [<span data-ttu-id="32b59-188">SQL 伺服器資料類型和ADO.NET</span><span class="sxs-lookup"><span data-stu-id="32b59-188">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- <span data-ttu-id="32b59-189">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="32b59-189">[ADO.NET Overview](../ado-net-overview.md)</span></span>
