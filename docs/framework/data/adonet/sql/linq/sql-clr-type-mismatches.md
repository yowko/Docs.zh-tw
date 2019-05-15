---
title: SQL-CLR 類型不符
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: e51d999d5fcaf8180b4ea5189a3db9b6143a57db
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582727"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="45bfb-102">SQL-CLR 類型不符</span><span class="sxs-lookup"><span data-stu-id="45bfb-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="45bfb-103">會自動執行物件模型 (Object Model) 與 SQL Server 之間大部分的轉譯作業。</span><span class="sxs-lookup"><span data-stu-id="45bfb-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="45bfb-104">不過，在某些情況下，還是無法進行精確的轉譯。</span><span class="sxs-lookup"><span data-stu-id="45bfb-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="45bfb-105">下列各節將摘要列出 Common Language Runtime (CLR) 型別與 SQL Server 資料庫型別之間的這些主要不符。</span><span class="sxs-lookup"><span data-stu-id="45bfb-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="45bfb-106">您可以找到更多特定型別對應和在函式轉譯詳細[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)並[Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) and [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="45bfb-107">資料類型</span><span class="sxs-lookup"><span data-stu-id="45bfb-107">Data Types</span></span>

<span data-ttu-id="45bfb-108">CLR 與 SQL Server 之間的轉譯會在查詢傳送至資料庫，以及結果傳回給物件模型時進行。</span><span class="sxs-lookup"><span data-stu-id="45bfb-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="45bfb-109">例如，下列 Transact-SQL 查詢需要進行兩種值轉換：</span><span class="sxs-lookup"><span data-stu-id="45bfb-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="45bfb-110">您必須先指定 Transact-SQL 參數的值，然後才能在 SQL Server 上執行查詢。</span><span class="sxs-lookup"><span data-stu-id="45bfb-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="45bfb-111">在此範例中，`id` 參數值必須先從 CLR <xref:System.Int32?displayProperty=nameWithType> 型別轉譯成 SQL Server `INT` 型別，如此資料庫才能了解其值為何。</span><span class="sxs-lookup"><span data-stu-id="45bfb-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="45bfb-112">然後，為了擷取結果，SQL Server `DateOfBirth` 資料行必須從 SQL Server `DATETIME` 型別轉譯成 CLR <xref:System.DateTime?displayProperty=nameWithType> 型別，以便用於物件模型中。</span><span class="sxs-lookup"><span data-stu-id="45bfb-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="45bfb-113">在此範例中，CLR 物件模型與 SQL Server 資料庫中的型別都具有自然對應。</span><span class="sxs-lookup"><span data-stu-id="45bfb-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="45bfb-114">但是，這種情況不一定永遠成立。</span><span class="sxs-lookup"><span data-stu-id="45bfb-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="45bfb-115">遺漏對應型別</span><span class="sxs-lookup"><span data-stu-id="45bfb-115">Missing Counterparts</span></span>

<span data-ttu-id="45bfb-116">下列型別沒有合理的對應型別。</span><span class="sxs-lookup"><span data-stu-id="45bfb-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="45bfb-117">CLR <xref:System> 命名空間 (Namespace) 中的不符：</span><span class="sxs-lookup"><span data-stu-id="45bfb-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="45bfb-118">**不帶正負號的整數**。</span><span class="sxs-lookup"><span data-stu-id="45bfb-118">**Unsigned integers**.</span></span> <span data-ttu-id="45bfb-119">這些型別通常會對應至大小較大且帶正負號的對應型別，以避免溢位。</span><span class="sxs-lookup"><span data-stu-id="45bfb-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="45bfb-120">常值可能會轉換為大小相同或較小的帶正負號數值 (以值為基礎)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="45bfb-121">**布林**。</span><span class="sxs-lookup"><span data-stu-id="45bfb-121">**Boolean**.</span></span> <span data-ttu-id="45bfb-122">這些型別可以對應至一個位元或是較大的數值或字串。</span><span class="sxs-lookup"><span data-stu-id="45bfb-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="45bfb-123">常值可能會對應至評估為等值的運算式 (例如，SQL 中的 `1=1` 在 CLS 中為 `True`)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="45bfb-124">**TimeSpan**。</span><span class="sxs-lookup"><span data-stu-id="45bfb-124">**TimeSpan**.</span></span> <span data-ttu-id="45bfb-125">這種型別代表兩個 `DateTime` 值之間的差異，而且不會對應至 SQL Server 的 `timestamp`。</span><span class="sxs-lookup"><span data-stu-id="45bfb-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="45bfb-126">在某些情況下，CLR <xref:System.TimeSpan?displayProperty=nameWithType> 可能也會對應至 SQL Server `TIME` 型別。</span><span class="sxs-lookup"><span data-stu-id="45bfb-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="45bfb-127">SQL Server `TIME` 型別只能用於代表小於 24 小時的正值。</span><span class="sxs-lookup"><span data-stu-id="45bfb-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="45bfb-128">CLR <xref:System.TimeSpan> 具有較大的範圍。</span><span class="sxs-lookup"><span data-stu-id="45bfb-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="45bfb-129">中的 SQL Server 特定.NET Framework 型別<xref:System.Data.SqlTypes>不包含在這項比較。</span><span class="sxs-lookup"><span data-stu-id="45bfb-129">SQL Server-specific .NET Framework types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="45bfb-130">SQL Server 中的不符：</span><span class="sxs-lookup"><span data-stu-id="45bfb-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="45bfb-131">**固定長度字元型別**。</span><span class="sxs-lookup"><span data-stu-id="45bfb-131">**Fixed length character types**.</span></span> <span data-ttu-id="45bfb-132">TRANSACT-SQL 會區分 Unicode 與非 Unicode 類別和每個類別中有三種不同類型： 固定長度`nchar` / `char`，可變長度`nvarchar` / `varchar`，及較大型`ntext` / `text`。</span><span class="sxs-lookup"><span data-stu-id="45bfb-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="45bfb-133">固定長度字元型別可以對應至 CLR <xref:System.Char?displayProperty=nameWithType> 型別供字元擷取之用，但它們在轉換時和行為上並不會真的對應至這個型別。</span><span class="sxs-lookup"><span data-stu-id="45bfb-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="45bfb-134">**位元**。</span><span class="sxs-lookup"><span data-stu-id="45bfb-134">**Bit**.</span></span> <span data-ttu-id="45bfb-135">雖然 `bit` 定義域與 `Nullable<Boolean>` 具有相同數目的值，但是它們是不同的型別。</span><span class="sxs-lookup"><span data-stu-id="45bfb-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="45bfb-136">`Bit` 接受的值`1`並`0`而不是`true` / `false`，並不能當做布林運算式的對等用法。</span><span class="sxs-lookup"><span data-stu-id="45bfb-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="45bfb-137">**時間戳記**。</span><span class="sxs-lookup"><span data-stu-id="45bfb-137">**Timestamp**.</span></span> <span data-ttu-id="45bfb-138">與 CLR <xref:System.TimeSpan?displayProperty=nameWithType> 型別不同的是，SQL Server `TIMESTAMP` 型別代表資料庫針對每次更新所產生的 8 位元組唯一數字，因此不是根據 <xref:System.DateTime> 值之間的差異。</span><span class="sxs-lookup"><span data-stu-id="45bfb-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="45bfb-139">**金錢**並**SmallMoney**。</span><span class="sxs-lookup"><span data-stu-id="45bfb-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="45bfb-140">這些型別可以對應至 <xref:System.Decimal>，但是它們基本上是不同的型別，而且伺服器架構函式和轉換也會將它們視為不同的型別。</span><span class="sxs-lookup"><span data-stu-id="45bfb-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="45bfb-141">多重對應</span><span class="sxs-lookup"><span data-stu-id="45bfb-141">Multiple Mappings</span></span>

<span data-ttu-id="45bfb-142">可對應至一或多個 CLR 資料型別的 SQL Server 資料型別有許多種。</span><span class="sxs-lookup"><span data-stu-id="45bfb-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="45bfb-143">可對應至一或多個 SQL Server 資料型別的 CLR 型別也有許多種。</span><span class="sxs-lookup"><span data-stu-id="45bfb-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="45bfb-144">雖然 LINQ to SQL 可能會支援某種對應，但是這並不表示在 CLR 與 SQL Server 之間對應的兩種型別在精確度、範圍和語意 (Semantics) 方面就是完美的相符。</span><span class="sxs-lookup"><span data-stu-id="45bfb-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="45bfb-145">在任何或所有這些維度 (Dimension) 中，某些對應可能會包含差異。</span><span class="sxs-lookup"><span data-stu-id="45bfb-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="45bfb-146">您可以找到關於這些可能差異的詳細資料在各種對應可能性[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="45bfb-147">使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="45bfb-147">User-defined Types</span></span>

<span data-ttu-id="45bfb-148">使用者定義 CLR 型別的設計目的是協助填補型別系統之間的差距。</span><span class="sxs-lookup"><span data-stu-id="45bfb-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="45bfb-149">不過，它們也產生型別版本控制的相關問題。</span><span class="sxs-lookup"><span data-stu-id="45bfb-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="45bfb-150">用戶端上的版本變更可能會與資料庫伺服器上儲存的型別變更不符。</span><span class="sxs-lookup"><span data-stu-id="45bfb-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="45bfb-151">任何這類變更都會導致另一項類型不符問題，即型別語意不相符，因而產生版本差距。</span><span class="sxs-lookup"><span data-stu-id="45bfb-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="45bfb-152">隨著後續版本重新調整繼承階層架構 (Inheritance Hierarchy)，情況會越來越複雜。</span><span class="sxs-lookup"><span data-stu-id="45bfb-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="45bfb-153">運算式語意</span><span class="sxs-lookup"><span data-stu-id="45bfb-153">Expression Semantics</span></span>

<span data-ttu-id="45bfb-154">除了 CLR 與資料庫型別之間的配對錯誤以外，運算式也會使得不相符的情況更複雜。</span><span class="sxs-lookup"><span data-stu-id="45bfb-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="45bfb-155">運算子語意、函式語意、隱含型別轉換和優先順序規則中的不符處都必須納入考慮。</span><span class="sxs-lookup"><span data-stu-id="45bfb-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="45bfb-156">下列各副小節說明看似相似運算式之間的不符處。</span><span class="sxs-lookup"><span data-stu-id="45bfb-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="45bfb-157">雖然可以產生在語意上與某個 CLR 運算式相等的 SQL 運算式，</span><span class="sxs-lookup"><span data-stu-id="45bfb-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="45bfb-158">但是 CLR 使用者不一定能清楚看出看似相似運算式之間的語意差異，因此也就不知道語意對等關係的變更是不是必要。</span><span class="sxs-lookup"><span data-stu-id="45bfb-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="45bfb-159">在評估運算式來產生一組值時，這個問題特別重要。</span><span class="sxs-lookup"><span data-stu-id="45bfb-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="45bfb-160">差異是否明顯可能要視資料而定，而且可能很難在編碼和偵錯期間就識別出差異。</span><span class="sxs-lookup"><span data-stu-id="45bfb-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="45bfb-161">Null 語意</span><span class="sxs-lookup"><span data-stu-id="45bfb-161">Null Semantics</span></span>

<span data-ttu-id="45bfb-162">SQL 運算式為布林值運算式提供三種邏輯值。</span><span class="sxs-lookup"><span data-stu-id="45bfb-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="45bfb-163">結果可以是 true、false 或 null。</span><span class="sxs-lookup"><span data-stu-id="45bfb-163">The result can be true, false, or null.</span></span> <span data-ttu-id="45bfb-164">另一方面，CLR 只會針對牽涉到 null 值的比較，指定兩種布林值結果。</span><span class="sxs-lookup"><span data-stu-id="45bfb-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="45bfb-165">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="45bfb-165">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="45bfb-166">採用兩種值的結果時可能會發生類似問題。</span><span class="sxs-lookup"><span data-stu-id="45bfb-166">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="45bfb-167">在上一個案例中，雖然產生的 SQL 會有對等的行為，但是轉譯作業可能不會精確地反映您的意圖。</span><span class="sxs-lookup"><span data-stu-id="45bfb-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="45bfb-168">不會造成C#`null`或 Visual Basic`nothing`上 SQL 的比較語意。</span><span class="sxs-lookup"><span data-stu-id="45bfb-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="45bfb-169">比較運算子會轉譯為語法上的 SQL 對等用法。</span><span class="sxs-lookup"><span data-stu-id="45bfb-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="45bfb-170">而語意會反映伺服器所定義的 SQL 語意或連接設定。</span><span class="sxs-lookup"><span data-stu-id="45bfb-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="45bfb-171">在預設 SQL Server 設定下，兩個 null 值會視為不相等的值 (雖然您可以變更設定來變更語意)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="45bfb-172">不過，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在轉譯查詢時並不會考慮伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="45bfb-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="45bfb-173">結果為常值 `null` (`nothing`) 的比較作業會轉譯為適當的 SQL 版本 (`is null` 或 `is not null`)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="45bfb-174">定序 (Collation) 中的值 `null` (`nothing`) 是由 SQL Server 所定義，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不會變更這個定序。</span><span class="sxs-lookup"><span data-stu-id="45bfb-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="45bfb-175">型別轉換和提升</span><span class="sxs-lookup"><span data-stu-id="45bfb-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="45bfb-176">SQL 支援在運算式中使用一組豐富的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="45bfb-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="45bfb-177">C# 中的類似運算式則需要明確轉換 (Cast)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="45bfb-178">例如: </span><span class="sxs-lookup"><span data-stu-id="45bfb-178">For example:</span></span>

- <span data-ttu-id="45bfb-179">在 SQL 中不需要任何明確轉換 (Cast)，就可以比較 `Nvarchar` 和 `DateTime` 型別，在 C# 中則需要明確轉換 (Conversion)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="45bfb-180">在 SQL 中 `Decimal` 會隱含地轉換為 `DateTime`。</span><span class="sxs-lookup"><span data-stu-id="45bfb-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="45bfb-181">C# 則不允許隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="45bfb-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="45bfb-182">同樣地，因為基礎的一組型別不同，所以 Transact-SQL 中的型別優先順序也會與 C# 中的型別優先順序不同。</span><span class="sxs-lookup"><span data-stu-id="45bfb-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="45bfb-183">事實上，優先順序清單之間並沒有明確的子集/超集關聯性 (Relationship)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="45bfb-184">例如，將 `nvarchar` 與 `varchar` 比較會將 `varchar` 運算式隱含地轉換為 `nvarchar`。</span><span class="sxs-lookup"><span data-stu-id="45bfb-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="45bfb-185">CLR 不提供對等的提升作業。</span><span class="sxs-lookup"><span data-stu-id="45bfb-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="45bfb-186">在簡單案例中，這些差異會使得包含轉換的 CLR 運算式對於對應的 SQL 運算式而言是多餘的。</span><span class="sxs-lookup"><span data-stu-id="45bfb-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="45bfb-187">更重要的是，SQL 運算式的中繼結果可能會隱含地提升成在 C# l 中沒有精確對應型別的型別，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="45bfb-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="45bfb-188">整體來說，這類運算式的測試、偵錯和驗證作業會對使用者造成沈重的負擔。</span><span class="sxs-lookup"><span data-stu-id="45bfb-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="45bfb-189">定序</span><span class="sxs-lookup"><span data-stu-id="45bfb-189">Collation</span></span>

<span data-ttu-id="45bfb-190">Transact-SQL 支援以字元字串型別的附註形式進行明確定序。</span><span class="sxs-lookup"><span data-stu-id="45bfb-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="45bfb-191">這些定序會決定特定比較的有效性。</span><span class="sxs-lookup"><span data-stu-id="45bfb-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="45bfb-192">例如，如果比較具有不同明確定序的兩個資料行，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="45bfb-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="45bfb-193">使用較簡化的 CTS 字串型別就不會造成這類錯誤。</span><span class="sxs-lookup"><span data-stu-id="45bfb-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="45bfb-194">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="45bfb-194">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="45bfb-195">實際上，定序子項子句會建立*限制型別*這不是可取代。</span><span class="sxs-lookup"><span data-stu-id="45bfb-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="45bfb-196">同樣地，這些型別系統的排序次序也有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="45bfb-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="45bfb-197">這項差異會影響結果的排序。</span><span class="sxs-lookup"><span data-stu-id="45bfb-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="45bfb-198">所有 16 位元組上的 <xref:System.Guid> 都會依詞彙編篡順序來排序 (`IComparable()`)，而 T-SQL 會依下列順序比較 GUID：node(10-15)、clock-seq(8-9)、time-high(6-7)、time-mid(4-5)、time-low(0-3)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="45bfb-199">在 SQL 7.0 中，這項排序作業會在 NT 產生的 GUID 具有這類八位元順序時執行。</span><span class="sxs-lookup"><span data-stu-id="45bfb-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="45bfb-200">這種方式可確保在相同節點叢集上產生的 GUID，會根據時間戳記連續出現。</span><span class="sxs-lookup"><span data-stu-id="45bfb-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="45bfb-201">這種方式同時也適用於建置索引 (「插入」現在變成「附加」，而不是隨機 IO)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="45bfb-202">後來在 Windows 中，這個順序基於隱私權考量被打亂了，但是 SQL 還是必須維護相容性。</span><span class="sxs-lookup"><span data-stu-id="45bfb-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="45bfb-203">因應措施是使用<xref:System.Data.SqlTypes.SqlGuid>而不是<xref:System.Guid>。</span><span class="sxs-lookup"><span data-stu-id="45bfb-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="45bfb-204">運算子和函式差異</span><span class="sxs-lookup"><span data-stu-id="45bfb-204">Operator and Function Differences</span></span>

<span data-ttu-id="45bfb-205">在本質上相等的運算子和函式，在語意上具有少許的差異。</span><span class="sxs-lookup"><span data-stu-id="45bfb-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="45bfb-206">例如：</span><span class="sxs-lookup"><span data-stu-id="45bfb-206">For example:</span></span>

- <span data-ttu-id="45bfb-207">C# 會根據邏輯運算子 (Logical Operator) `&&` 和 `||` 的運算元語彙順序，指定最少運算 (Short Circuit) 語意。</span><span class="sxs-lookup"><span data-stu-id="45bfb-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="45bfb-208">相反地，SQL 是針對集合架構查詢，因此可提供更多的自由讓最佳化工具決定執行順序。</span><span class="sxs-lookup"><span data-stu-id="45bfb-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="45bfb-209">下列是部分隱含意義：</span><span class="sxs-lookup"><span data-stu-id="45bfb-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="45bfb-210">語意上相等的轉譯，則必須 「`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="45bfb-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="45bfb-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="45bfb-211">`WHEN` …</span></span> <span data-ttu-id="45bfb-212">`THEN`「 SQL，以避免重設運算元執行順序中建構。</span><span class="sxs-lookup"><span data-stu-id="45bfb-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="45bfb-213">則鬆散轉譯為`AND` / `OR`運算子可能會導致未預期的錯誤，如果C#運算式依賴評估根據第一個運算元評估結果的第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="45bfb-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="45bfb-214">`Round()` .NET Framework 中，並在 T-SQL 中，函式會有不同的語意。</span><span class="sxs-lookup"><span data-stu-id="45bfb-214">`Round()` function has different semantics in .NET Framework and in T-SQL.</span></span>

- <span data-ttu-id="45bfb-215">在 CLR 中，字串的起始索引是 0，而在 SQL 中則是 1。</span><span class="sxs-lookup"><span data-stu-id="45bfb-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="45bfb-216">因此，任何具有索引的函式都需要進行索引轉譯。</span><span class="sxs-lookup"><span data-stu-id="45bfb-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="45bfb-217">CLR 支援浮點數的模數 (‘%’) 運算子，而 SQL 則不支援。</span><span class="sxs-lookup"><span data-stu-id="45bfb-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="45bfb-218">`Like` 運算子實際上會根據隱含轉換來取得自動多載。</span><span class="sxs-lookup"><span data-stu-id="45bfb-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="45bfb-219">雖然 `Like` 運算子是定義成對字元字串型別執行，但是將數值型別或 `DateTime` 型別等非字串型別進行隱含轉換後，同樣也可以使用 `Like`。</span><span class="sxs-lookup"><span data-stu-id="45bfb-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="45bfb-220">在 CTS 中，並沒有相等的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="45bfb-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="45bfb-221">因此，需要額外進行多載。</span><span class="sxs-lookup"><span data-stu-id="45bfb-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="45bfb-222">這個 `Like` 運算子行為僅適用於 C#，Visual Basic 的 `Like` 關鍵字仍未改變。</span><span class="sxs-lookup"><span data-stu-id="45bfb-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="45bfb-223">溢位則一律會在 SQL 中檢查但有明確指定在C#(不在 Visual Basic)，以避免發生繞回問題。</span><span class="sxs-lookup"><span data-stu-id="45bfb-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="45bfb-224">假設有三個整數資料行：C1、C2，和負責儲存 C1+C2 的 C3 (Update T Set C3 = C1 + C2)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- <span data-ttu-id="45bfb-225">SQL 執行對稱式算術捨入而.NET Framework 可讓您使用成雙。</span><span class="sxs-lookup"><span data-stu-id="45bfb-225">SQL performs symmetric arithmetic rounding while .NET Framework uses banker’s rounding.</span></span> <span data-ttu-id="45bfb-226">如需詳細資訊，請參閱知識庫文件 196652。</span><span class="sxs-lookup"><span data-stu-id="45bfb-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="45bfb-227">根據預設，在通用地區設定 (Locale) 中，SQL 中的字元字串比較作業不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="45bfb-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="45bfb-228">在 Visual Basic 和 C# 中，則會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="45bfb-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="45bfb-229">例如， `s == "Food"` (`s = "Food"` Visual Basic 中) 及`s == "Food"`可以產生不同的結果，如果`s`是`food`。</span><span class="sxs-lookup"><span data-stu-id="45bfb-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- <span data-ttu-id="45bfb-230">在 SQL 中套用至固定長度字元型別引數的運算子/函式，在語意上與套用至 CLR <xref:System.String?displayProperty=nameWithType> 的相同運算子/函式有顯著不同。</span><span class="sxs-lookup"><span data-stu-id="45bfb-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="45bfb-231">這也可以視為上面有關型別的一節中所討論之遺漏對應型別問題的延伸。</span><span class="sxs-lookup"><span data-stu-id="45bfb-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     <span data-ttu-id="45bfb-232">將字串串連時也會發生類似問題。</span><span class="sxs-lookup"><span data-stu-id="45bfb-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="45bfb-233">總而言之，CLR 運算式可能需要進行迂迴的轉譯，而且可能需要有其他運算子/函式，才能公開SQL 功能。</span><span class="sxs-lookup"><span data-stu-id="45bfb-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="45bfb-234">型別轉換</span><span class="sxs-lookup"><span data-stu-id="45bfb-234">Type Casting</span></span>

<span data-ttu-id="45bfb-235">在 C# 和 SQL 中，使用者可以使用明確型別轉換 (`Cast` 和 `Convert`) 來覆寫運算式的預設語意。</span><span class="sxs-lookup"><span data-stu-id="45bfb-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="45bfb-236">不過，是否跨型別系統界限公開這個功能，乃是一個兩難的選擇。</span><span class="sxs-lookup"><span data-stu-id="45bfb-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="45bfb-237">提供所需語意的 SQL 轉換 (Cast) 無法輕易地轉譯為對應的 C# 轉換 (Cast)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="45bfb-238">另一方面，C# 轉換 (Cast) 也會因為類型不符、遺漏對應型別以及型別優先順序階層架構不同等問題，而無法直接轉譯為對等的 SQL 轉換 (Cast)。</span><span class="sxs-lookup"><span data-stu-id="45bfb-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="45bfb-239">因此，在公開型別系統不符處與損失運算式強大功能之間，需要有所取捨。</span><span class="sxs-lookup"><span data-stu-id="45bfb-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="45bfb-240">在其他情況下，這兩個定義域的運算式驗證作業可能都不需要進行型別轉換，但是也可能需要進行型別轉換以確保非預設對應已正確套用至運算式。</span><span class="sxs-lookup"><span data-stu-id="45bfb-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="45bfb-241">效能問題</span><span class="sxs-lookup"><span data-stu-id="45bfb-241">Performance Issues</span></span>

<span data-ttu-id="45bfb-242">帳戶處理的某些 SQL Server CLR 型別差異可能會導致效能降低時跨越 CLR 與 SQL Server 型別系統。</span><span class="sxs-lookup"><span data-stu-id="45bfb-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="45bfb-243">影響效能之案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="45bfb-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="45bfb-244">強制限制邏輯 and/or 運算子的評估順序</span><span class="sxs-lookup"><span data-stu-id="45bfb-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="45bfb-245">如果產生的 SQL 會強制限制述詞的評估順序，SQL 最佳化工具的功能會無法發揮。</span><span class="sxs-lookup"><span data-stu-id="45bfb-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="45bfb-246">型別轉換 (不論是透過 CLR 編譯器還是物件關聯式查詢實作進行) 可以減少索引的使用。</span><span class="sxs-lookup"><span data-stu-id="45bfb-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="45bfb-247">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="45bfb-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="45bfb-248">請考慮運算式 `(s = SOME_STRING_CONSTANT)` 的轉譯。</span><span class="sxs-lookup"><span data-stu-id="45bfb-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="45bfb-249">除了語意差異以外，請務必考量在 SQL Server 與 CLR 型別系統之間跨越時，對效能造成的影響。</span><span class="sxs-lookup"><span data-stu-id="45bfb-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="45bfb-250">如果是大型資料集，這類效能問題可能會決定部署應用程式的可行性。</span><span class="sxs-lookup"><span data-stu-id="45bfb-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="45bfb-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45bfb-251">See also</span></span>

- [<span data-ttu-id="45bfb-252">背景資訊</span><span class="sxs-lookup"><span data-stu-id="45bfb-252">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
