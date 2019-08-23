---
title: 處理 Null 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 077cfd9b90df130e0a6090637d5dbd70a70930b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938191"
---
# <a name="handling-null-values"></a><span data-ttu-id="e023c-102">處理 Null 值</span><span class="sxs-lookup"><span data-stu-id="e023c-102">Handling Null Values</span></span>
<span data-ttu-id="e023c-103">當資料行中的值未知或遺失時，便會使用關聯式資料庫中的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e023c-103">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="e023c-104">Null 既不是空字串 (針對字元或 datetime 資料型別)，也不是零值 (針對數值資料型別)。</span><span class="sxs-lookup"><span data-stu-id="e023c-104">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="e023c-105">根據 ANSI SQL-92 規格的內容，對所有的資料型別而言，Null 必須都是相同的，以便可一致處理所有的 Null。</span><span class="sxs-lookup"><span data-stu-id="e023c-105">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="e023c-106">藉由實作 <xref:System.Data.SqlTypes> 介面，<xref:System.Data.SqlTypes.INullable> 命名空間可以提供 Null 語意。</span><span class="sxs-lookup"><span data-stu-id="e023c-106">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="e023c-107"><xref:System.Data.SqlTypes> 中的每個資料型別都具有自己的 `IsNull` 屬性及 `Null` 值，而該值可以指派給該資料型別的執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="e023c-107">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e023c-108">.NET Framework 2.0 版開始支援可為 Null 型別，這讓程式設計人員得以擴充實值型別，以表示基礎型別所有的值。</span><span class="sxs-lookup"><span data-stu-id="e023c-108">The .NET Framework version 2.0 introduced support for nullable types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="e023c-109">這些 CLR 可為 Null 的型別代表 <xref:System.Nullable> 結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e023c-109">These CLR nullable types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="e023c-110">當實質型別為 boxed 和 unboxed 時，這項功能特別有用，可強化與物件型別的相容性。</span><span class="sxs-lookup"><span data-stu-id="e023c-110">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="e023c-111">CLR 可為 Null 的型別不適用於儲存資料庫 Null，因為 ANSI SQL Null 的行為方式與 `null` 參考不同 (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="e023c-111">CLR nullable types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="e023c-112">若要使用資料庫 ANSI SQL Null 值，請利用 <xref:System.Data.SqlTypes> Null 而非 <xref:System.Nullable>。</span><span class="sxs-lookup"><span data-stu-id="e023c-112">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="e023c-113">如需在 Visual Basic 中使用 CLR 可為 null 型別的詳細資訊, 請參閱[可為 null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)的實值型別, 以及C# [使用可為 null](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)型別的</span><span class="sxs-lookup"><span data-stu-id="e023c-113">For more information on working with CLR nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Using Nullable Types](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="e023c-114">Null 及三種值的邏輯</span><span class="sxs-lookup"><span data-stu-id="e023c-114">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="e023c-115">在資料行定義中允許 Null 值會將三種值的邏輯引進應用程式。</span><span class="sxs-lookup"><span data-stu-id="e023c-115">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="e023c-116">比較可評估為下列三個條件之一：</span><span class="sxs-lookup"><span data-stu-id="e023c-116">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="e023c-117">True</span><span class="sxs-lookup"><span data-stu-id="e023c-117">True</span></span>  
  
- <span data-ttu-id="e023c-118">偽</span><span class="sxs-lookup"><span data-stu-id="e023c-118">False</span></span>  
  
- <span data-ttu-id="e023c-119">不明</span><span class="sxs-lookup"><span data-stu-id="e023c-119">Unknown</span></span>  
  
 <span data-ttu-id="e023c-120">因為 Null 會視為 Unknown，所以比較兩個 Null 值時，並不會視為相等的。</span><span class="sxs-lookup"><span data-stu-id="e023c-120">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="e023c-121">在使用算術運算子的運算式中，如果有任何運算元為 Null，其結果也會是 Null。</span><span class="sxs-lookup"><span data-stu-id="e023c-121">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="e023c-122">Null 及 SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="e023c-122">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="e023c-123">任何 <xref:System.Data.SqlTypes> 之間的比較都將傳回 <xref:System.Data.SqlTypes.SqlBoolean>。</span><span class="sxs-lookup"><span data-stu-id="e023c-123">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="e023c-124">每個 `IsNull` 的 `SqlType` 函式都會傳回 <xref:System.Data.SqlTypes.SqlBoolean>，並可用於檢查是否有 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e023c-124">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="e023c-125">下列 True 值資料表顯示存在 Null 值時，AND、OR 及 NOT 運算子將如何運作。</span><span class="sxs-lookup"><span data-stu-id="e023c-125">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="e023c-126">(T=true、F=false 及 U=unknown 或 Null)。</span><span class="sxs-lookup"><span data-stu-id="e023c-126">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="e023c-127">![事實資料表](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="e023c-127">![Truth Table](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="e023c-128">瞭解 ANSI_NULLS 選項</span><span class="sxs-lookup"><span data-stu-id="e023c-128">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="e023c-129"><xref:System.Data.SqlTypes> 提供的語意與在 SQL Server 中設定 ANSI_NULLS 選項時的語意相同。</span><span class="sxs-lookup"><span data-stu-id="e023c-129"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="e023c-130">如果任何運算元或引數為 null (屬性&#124; `IsNull`除外), 則所有算術運算子 (+、-、\*、/、%)、位運算子 (~、&、) 和大部分函數都會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="e023c-130">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, &#124;), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="e023c-131">ANSI SQL-92 標準不支援 WHERE 子句中的*columnName* = Null。</span><span class="sxs-lookup"><span data-stu-id="e023c-131">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="e023c-132">在 SQL Server 中，ANSI_NULLS 選項可控制資料庫中的預設 Null 屬性及針對 Null 值的比較評估。</span><span class="sxs-lookup"><span data-stu-id="e023c-132">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="e023c-133">如果啟用 ANSI_NULLS (預設值)，則當測試 Null 值時，必須在運算式中使用 IS NULL 運算子。</span><span class="sxs-lookup"><span data-stu-id="e023c-133">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="e023c-134">例如，當啟用 ANSI_NULLS 時，下列比較永遠會產生 Unknown：</span><span class="sxs-lookup"><span data-stu-id="e023c-134">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```  
colname > NULL  
```  
  
 <span data-ttu-id="e023c-135">對包含 Null 值的變數進行比較也會產生 Unknown：</span><span class="sxs-lookup"><span data-stu-id="e023c-135">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```  
colname > @MyVariable  
```  
  
 <span data-ttu-id="e023c-136">使用 IS NULL 或 IS NOT NULL 述詞來測試 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e023c-136">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="e023c-137">如此會增加 WHERE 子句的複雜性。</span><span class="sxs-lookup"><span data-stu-id="e023c-137">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="e023c-138">例如，AdventureWorks Customer 資料表中的 TerritoryID 資料行允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e023c-138">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="e023c-139">如果 SELECT 陳述式除測試其他項目之外，還要測試 Null 值，則其必須包括 IS NULL 述詞：</span><span class="sxs-lookup"><span data-stu-id="e023c-139">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="e023c-140">如果在 SQL Server 中將 ANSI_NULLS 設為停用，則可以建立使用相等運算子的運算式，以與 Null 進行比較。</span><span class="sxs-lookup"><span data-stu-id="e023c-140">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="e023c-141">不過，您無法阻止不同連接設定該連接的 Null 選項。</span><span class="sxs-lookup"><span data-stu-id="e023c-141">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="e023c-142">不論連接的 ANSI_NULLS 設定為何，都可以使用 IS NULL 來測試 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e023c-142">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="e023c-143">在 `DataSet` 中不支援將 ANSI_NULLS 設為停用，因為它永遠會遵循 ANSI SQL-92 標準來處理 <xref:System.Data.SqlTypes> 中的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e023c-143">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="e023c-144">指派 Null 值</span><span class="sxs-lookup"><span data-stu-id="e023c-144">Assigning Null Values</span></span>  
 <span data-ttu-id="e023c-145">Null 值較特殊，其儲存及指派語意在不同類型系統及儲存系統之間會有所不同。</span><span class="sxs-lookup"><span data-stu-id="e023c-145">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="e023c-146">`Dataset` 是設計為與不同類型及儲存系統搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e023c-146">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="e023c-147">本節將說明 Null 語意，其可指派 Null 值給跨不同類型系統之 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="e023c-147">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="e023c-148">此指派針對任何型別的 `DataColumn` 都有效。</span><span class="sxs-lookup"><span data-stu-id="e023c-148">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="e023c-149">如果型別實作 `INullable`，則 `DBNull.Value` 會強制轉型為適當的強型別 (Strongly Typed) Null 值。</span><span class="sxs-lookup"><span data-stu-id="e023c-149">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="e023c-150">所有 <xref:System.Data.SqlTypes> 資料型別都可實作 `INullable`。</span><span class="sxs-lookup"><span data-stu-id="e023c-150">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="e023c-151">如果使用隱含轉換運算子，將強型別 Null 值轉換成資料行的資料型別，指派就應該能夠順利完成。</span><span class="sxs-lookup"><span data-stu-id="e023c-151">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="e023c-152">否則，將擲回無效轉換例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e023c-152">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="e023c-153">如果 'null' 是指定之 `DataColumn` 資料型別的合法值，它就會強制轉型為與 `DbNull.Value` 型別 (`Null`) 相關聯的適當 `INullable` 或 `SqlType.Null`。</span><span class="sxs-lookup"><span data-stu-id="e023c-153">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="e023c-154">若為 UDT 資料行，則永遠會依據與 `DataColumn` 相關聯的型別來儲存 Null。</span><span class="sxs-lookup"><span data-stu-id="e023c-154">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="e023c-155">請考量下列情況：UDT 與不實作 `DataColumn` 的 `INullable` (而其子類別實作) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="e023c-155">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="e023c-156">在此情況下，如果指派了與衍生類別相關聯的強型別 Null 值，它就會儲存為不具型別的 `DbNull.Value`，因為 Null 儲存永遠會與 DataColumn 的資料型別一致。</span><span class="sxs-lookup"><span data-stu-id="e023c-156">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e023c-157">目前在 `Nullable<T>` 中不支援 <xref:System.Nullable> 或 `DataSet` 結構。</span><span class="sxs-lookup"><span data-stu-id="e023c-157">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="e023c-158">多個資料行 (資料列) 指派</span><span class="sxs-lookup"><span data-stu-id="e023c-158">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="e023c-159">`DataTable.Add`、`DataTable.LoadDataRow` 或其他可接受對應至資料列之 <xref:System.Data.DataRow.ItemArray%2A> 的 API，會將 'null' 對應至 DataColumn 的預設值。</span><span class="sxs-lookup"><span data-stu-id="e023c-159">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="e023c-160">如果陣列中的物件包含 `DbNull.Value` 或其強型別的對應項，則會套用上述相同規則。</span><span class="sxs-lookup"><span data-stu-id="e023c-160">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="e023c-161">此外，下列規則可套用至 `DataRow.["columnName"]` Null 指派的執行個體：</span><span class="sxs-lookup"><span data-stu-id="e023c-161">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="e023c-162">除了強型別 null `DbNull.Value`資料行 (其為適當的強型別 null 值) 以外, 預設的預設值為。</span><span class="sxs-lookup"><span data-stu-id="e023c-162">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="e023c-163">在序列化為 XML 檔案期間永遠不會寫出 Null 值 (如同在 xsi:nil 中)。</span><span class="sxs-lookup"><span data-stu-id="e023c-163">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="e023c-164">在序列化為 XML 時，永遠會寫出所有非 Null 值 (包括預設值)。</span><span class="sxs-lookup"><span data-stu-id="e023c-164">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="e023c-165">這與 XSD/XML 語意不同，在 XSD/XML 語意中 Null 值 (xsi:nil) 是明確的，而預設值是隱含的 (如果不存在於 XML 中，則驗證剖析器可以從相關聯的 XSD 結構描述中取得它)。</span><span class="sxs-lookup"><span data-stu-id="e023c-165">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="e023c-166">`DataTable` 的情況則相反：Null 值是隱含的，而預設值則是明確的。</span><span class="sxs-lookup"><span data-stu-id="e023c-166">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="e023c-167">針對從 XML 輸入讀取之資料列的所有遺漏資料行值都會指派 NULL。</span><span class="sxs-lookup"><span data-stu-id="e023c-167">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="e023c-168">使用 <xref:System.Data.DataTable.NewRow%2A> 或類似方法建立的資料列會指派為 DataColumn 的預設值。</span><span class="sxs-lookup"><span data-stu-id="e023c-168">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="e023c-169"><xref:System.Data.DataRow.IsNull%2A> 方法會針對 `true` 和 `DbNull.Value` 傳回 `INullable.Null`。</span><span class="sxs-lookup"><span data-stu-id="e023c-169">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="e023c-170">指派 Null 值</span><span class="sxs-lookup"><span data-stu-id="e023c-170">Assigning Null Values</span></span>  
 <span data-ttu-id="e023c-171">任何 <xref:System.Data.SqlTypes> 執行個體的預設值都為 Null。</span><span class="sxs-lookup"><span data-stu-id="e023c-171">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="e023c-172"><xref:System.Data.SqlTypes> 中的 Null 是型別特定的，因此無法由單一值 (如 `DbNull`) 表示。</span><span class="sxs-lookup"><span data-stu-id="e023c-172">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="e023c-173">請使用 `IsNull` 屬性來檢查 Null。</span><span class="sxs-lookup"><span data-stu-id="e023c-173">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="e023c-174">Null 值可指派給 <xref:System.Data.DataColumn>，如下列程式碼範例中所示：</span><span class="sxs-lookup"><span data-stu-id="e023c-174">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="e023c-175">您可直接將 Null 值指派給 `SqlTypes` 變數，而不會觸發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e023c-175">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e023c-176">範例</span><span class="sxs-lookup"><span data-stu-id="e023c-176">Example</span></span>  
 <span data-ttu-id="e023c-177">下列程式碼範例會建立 <xref:System.Data.DataTable>，其包含兩個定義為 <xref:System.Data.SqlTypes.SqlInt32> 及 <xref:System.Data.SqlTypes.SqlString> 的資料行。</span><span class="sxs-lookup"><span data-stu-id="e023c-177">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="e023c-178">程式碼會加入一個已知值的資料列及一個 Null 值的資料列，然後在 <xref:System.Data.DataTable> 中重複，以將值指派給變數並在主控台視窗中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="e023c-178">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="e023c-179">此範例會顯示出下列結果：</span><span class="sxs-lookup"><span data-stu-id="e023c-179">This example displays the following results:</span></span>  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="e023c-180">將 Null 值與 SqlType 及 CLR 型別進行比較</span><span class="sxs-lookup"><span data-stu-id="e023c-180">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="e023c-181">比較 Null 值時，瞭解 `Equals` 方法評估 <xref:System.Data.SqlTypes> 中 Null 值的方式，與其處理 CLR 型別之方式相比較的差異很重要。</span><span class="sxs-lookup"><span data-stu-id="e023c-181">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="e023c-182">所有 <xref:System.Data.SqlTypes>`Equals` 方法都是使用資料庫語意來評估 Null 值：如果其中一個值或兩個值同時為 Null，則該比較會產生 Null。</span><span class="sxs-lookup"><span data-stu-id="e023c-182">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="e023c-183">另一方面，針對兩個 `Equals` 使用 CLR <xref:System.Data.SqlTypes> 方法時，如果二者都為 Null，則會產生 True。</span><span class="sxs-lookup"><span data-stu-id="e023c-183">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="e023c-184">這反映出使用執行個體方法 (例如 CLR `String.Equals` 方法) 與使用靜態/共用方法 (`SqlString.Equals`) 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e023c-184">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="e023c-185">下列範例示範當針對每個方法傳遞一對 Null 值，然後傳遞一對空字串時，`SqlString.Equals` 方法及 `String.Equals` 方法之間結果的差異。</span><span class="sxs-lookup"><span data-stu-id="e023c-185">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="e023c-186">該程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e023c-186">The code produces the following output:</span></span>  
  
```  
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a><span data-ttu-id="e023c-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e023c-187">See also</span></span>

- [<span data-ttu-id="e023c-188">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e023c-188">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [<span data-ttu-id="e023c-189">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e023c-189">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
