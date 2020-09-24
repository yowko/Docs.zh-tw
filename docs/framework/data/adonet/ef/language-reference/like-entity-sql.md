---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: c4c2d6020e5355930dfa8880b0966dfe015baa51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161837"
---
# <a name="like-entity-sql"></a><span data-ttu-id="2b191-102">LIKE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b191-102">LIKE (Entity SQL)</span></span>

<span data-ttu-id="2b191-103">判斷特定字元 `String` 是否符合指定的模式。</span><span class="sxs-lookup"><span data-stu-id="2b191-103">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b191-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b191-104">Syntax</span></span>  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b191-105">引數</span><span class="sxs-lookup"><span data-stu-id="2b191-105">Arguments</span></span>  

 `match`  
 <span data-ttu-id="2b191-106">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]評估為的運算式 `String` 。</span><span class="sxs-lookup"><span data-stu-id="2b191-106">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="2b191-107">用來比對指定 `String` 的模式。</span><span class="sxs-lookup"><span data-stu-id="2b191-107">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="2b191-108">逸出字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-108">An escape character.</span></span>  
  
 <span data-ttu-id="2b191-109">NOT</span><span class="sxs-lookup"><span data-stu-id="2b191-109">NOT</span></span>  
 <span data-ttu-id="2b191-110">指定要否定 LIKE 的結果。</span><span class="sxs-lookup"><span data-stu-id="2b191-110">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b191-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b191-111">Return Value</span></span>  

 <span data-ttu-id="2b191-112">如果 `true` 符合此模式則為 `string`；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2b191-112">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b191-113">備註</span><span class="sxs-lookup"><span data-stu-id="2b191-113">Remarks</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2b191-114">使用 LIKE 運算子的運算式的評估方式，與使用相等的運算式做為篩選準則的方式大致相同。</span><span class="sxs-lookup"><span data-stu-id="2b191-114">expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="2b191-115">不過， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 使用 LIKE 運算子的運算式可以同時包含常值和萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-115">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="2b191-116">下表所述為模式 `string` 的語法。</span><span class="sxs-lookup"><span data-stu-id="2b191-116">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="2b191-117">萬用字元</span><span class="sxs-lookup"><span data-stu-id="2b191-117">Wildcard Character</span></span>|<span data-ttu-id="2b191-118">描述</span><span class="sxs-lookup"><span data-stu-id="2b191-118">Description</span></span>|<span data-ttu-id="2b191-119">範例</span><span class="sxs-lookup"><span data-stu-id="2b191-119">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="2b191-120">任何包含零個或多個字元的 `string`。</span><span class="sxs-lookup"><span data-stu-id="2b191-120">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="2b191-121">`title like '%computer%'` 尋找標題中任何位置包含單字的所有標題 `"computer"` 。</span><span class="sxs-lookup"><span data-stu-id="2b191-121">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="2b191-122">_ (底線)</span><span class="sxs-lookup"><span data-stu-id="2b191-122">_ (underscore)</span></span>|<span data-ttu-id="2b191-123">任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-123">Any single character.</span></span>|<span data-ttu-id="2b191-124">`firstname like '_ean'` 尋找結尾為 "的所有四個字母的名字 `"ean` ，例如 Dean 或小紅。</span><span class="sxs-lookup"><span data-stu-id="2b191-124">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="2b191-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="2b191-125">[ ]</span></span>|<span data-ttu-id="2b191-126">在指定範圍 ([a-f]) 或集合 ([abcdef]) 中的任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-126">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="2b191-127">`lastname like '[C-P]arsen'` 尋找結尾為 "arsen" 且開頭為 C 和 P 之間任何單一字元的姓氏，例如 Carsen 或 Larsen。</span><span class="sxs-lookup"><span data-stu-id="2b191-127">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="2b191-128">[^]</span><span class="sxs-lookup"><span data-stu-id="2b191-128">[^]</span></span>|<span data-ttu-id="2b191-129">不在指定範圍 ([^a-f]) 或集合 ([^abcdef]) 中的任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-129">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="2b191-130">`lastname like 'de[^l]%'` 尋找開頭為 "de" 且不包含 "l" 作為下列字母的所有姓氏。</span><span class="sxs-lookup"><span data-stu-id="2b191-130">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2b191-131">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 運算子和 ESCAPE 子句不可套用到 `System.DateTime` 或 `System.Guid` 值。</span><span class="sxs-lookup"><span data-stu-id="2b191-131">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="2b191-132">LIKE 支援 ASCII 模式比對和 Unicode 模式比對。</span><span class="sxs-lookup"><span data-stu-id="2b191-132">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="2b191-133">如果所有參數都是 ASCII 字元，便會執行 ASCII 模式比對。</span><span class="sxs-lookup"><span data-stu-id="2b191-133">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="2b191-134">如果有任何引數不是 Unicode 資料類型，所有引數都會轉換成 Unicode，然後執行 Unicode 模式比對。</span><span class="sxs-lookup"><span data-stu-id="2b191-134">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="2b191-135">使用 Unicode 配合 LIKE 時，尾端空白是有意義的；但是對於非 Unicode，尾端空白就無關重要了。</span><span class="sxs-lookup"><span data-stu-id="2b191-135">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="2b191-136">的模式字串語法與 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transact-sql 的語法相同。</span><span class="sxs-lookup"><span data-stu-id="2b191-136">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of Transact-SQL.</span></span>  
  
 <span data-ttu-id="2b191-137">模式中可以包含一般字元及萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-137">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="2b191-138">在模式比對期間，一般字元必須與字元 `string` 中所指定的字元完全相符。</span><span class="sxs-lookup"><span data-stu-id="2b191-138">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="2b191-139">不過，萬用字元可以符合任意字元字串片段。</span><span class="sxs-lookup"><span data-stu-id="2b191-139">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="2b191-140">配合萬用字元使用時，LIKE 運算子會比 = 和 != 字串比較運算子更有彈性。</span><span class="sxs-lookup"><span data-stu-id="2b191-140">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b191-141">如果您要針對特定的提供者，可以使用提供者專用的運算式。</span><span class="sxs-lookup"><span data-stu-id="2b191-141">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="2b191-142">不過其他提供者可能會以不同方式處理這類建構。</span><span class="sxs-lookup"><span data-stu-id="2b191-142">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="2b191-143">SqlServer 支援 [first-last] 和 [^first-last] 模式，前者會在最前與最後範圍之間恰好符合一個字元 (只能有一個字元相符)，後者則是在最前與最後範圍之外恰好符合一個字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-143">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="2b191-144">逸出</span><span class="sxs-lookup"><span data-stu-id="2b191-144">Escape</span></span>  

 <span data-ttu-id="2b191-145">使用 ESCAPE 子句可以搜尋包含一或多個先前章節表格中所述特殊萬用字元的字元字串。</span><span class="sxs-lookup"><span data-stu-id="2b191-145">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="2b191-146">舉例來講，假設有幾份文件的標題包含常值 "100%"，而您想要搜尋所有這些文件。</span><span class="sxs-lookup"><span data-stu-id="2b191-146">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="2b191-147">因為 percent (% ) 字元是萬用字元，所以您必須使用 escape 子句來將它 escape， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 才能成功執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="2b191-147">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="2b191-148">以下就是這項篩選的範例。</span><span class="sxs-lookup"><span data-stu-id="2b191-148">The following is an example of this filter.</span></span>  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="2b191-149">在這個搜尋運算式中，緊接在驚嘆號字元 (!) 後面的百分比萬用字元 (%) 會被視為常值，而不是萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-149">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="2b191-150">您可以使用任何字元作為 escape 字元 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ，但萬用字元和方括弧 (`[ ]`) 個字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-150">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="2b191-151">在前一個範例中，驚嘆號 (!) 字元是逸出字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-151">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b191-152">範例</span><span class="sxs-lookup"><span data-stu-id="2b191-152">Example</span></span>  

 <span data-ttu-id="2b191-153">下列兩個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 LIKE 和 ESCAPE 運算子來判斷特定的字元字串是否符合指定的模式。</span><span class="sxs-lookup"><span data-stu-id="2b191-153">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="2b191-154">第一個查詢會搜尋以 `Name` 字元開頭的 `Down_` 。</span><span class="sxs-lookup"><span data-stu-id="2b191-154">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="2b191-155">這個查詢使用了 ESCAPE 選項，因為底線 (`_`) 是萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-155">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="2b191-156">如果未指定 ESCAPE 選項，查詢會搜尋開頭為單字的任何 `Name` 值， `Down` 後面接著底線字元以外的任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="2b191-156">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="2b191-157">這些查詢是以 AdventureWorks Sales Model 為依據。</span><span class="sxs-lookup"><span data-stu-id="2b191-157">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b191-158">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="2b191-158">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2b191-159">依照 how [to：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式操作。</span><span class="sxs-lookup"><span data-stu-id="2b191-159">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2b191-160">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="2b191-160">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a><span data-ttu-id="2b191-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b191-161">See also</span></span>

- [<span data-ttu-id="2b191-162">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="2b191-162">Entity SQL Reference</span></span>](entity-sql-reference.md)
