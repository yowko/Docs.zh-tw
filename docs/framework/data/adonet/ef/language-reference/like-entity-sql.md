---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 58828b812ce374a664e4d232b707f22d5ca438c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912276"
---
# <a name="like-entity-sql"></a><span data-ttu-id="8bb41-102">LIKE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8bb41-102">LIKE (Entity SQL)</span></span>
<span data-ttu-id="8bb41-103">判斷特定字元 `String` 是否符合指定的模式。</span><span class="sxs-lookup"><span data-stu-id="8bb41-103">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb41-104">語法</span><span class="sxs-lookup"><span data-stu-id="8bb41-104">Syntax</span></span>  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8bb41-105">引數</span><span class="sxs-lookup"><span data-stu-id="8bb41-105">Arguments</span></span>  
 `match`  
 <span data-ttu-id="8bb41-106">評估為的`String`運算式。[!INCLUDE[esql](../../../../../../includes/esql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bb41-106">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="8bb41-107">用來比對指定 `String` 的模式。</span><span class="sxs-lookup"><span data-stu-id="8bb41-107">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="8bb41-108">逸出字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-108">An escape character.</span></span>  
  
 <span data-ttu-id="8bb41-109">NOT</span><span class="sxs-lookup"><span data-stu-id="8bb41-109">NOT</span></span>  
 <span data-ttu-id="8bb41-110">指定要否定 LIKE 的結果。</span><span class="sxs-lookup"><span data-stu-id="8bb41-110">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bb41-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8bb41-111">Return Value</span></span>  
 <span data-ttu-id="8bb41-112">如果 `true` 符合此模式則為 `string`；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8bb41-112">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bb41-113">備註</span><span class="sxs-lookup"><span data-stu-id="8bb41-113">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8bb41-114">使用 LIKE 運算子的運算式, 其評估方式與使用等式做為篩選準則的運算式大致相同。</span><span class="sxs-lookup"><span data-stu-id="8bb41-114">expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="8bb41-115">不過, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]使用 LIKE 運算子的運算式可以同時包含常值和萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-115">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="8bb41-116">下表所述為模式 `string` 的語法。</span><span class="sxs-lookup"><span data-stu-id="8bb41-116">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="8bb41-117">萬用字元</span><span class="sxs-lookup"><span data-stu-id="8bb41-117">Wildcard Character</span></span>|<span data-ttu-id="8bb41-118">描述</span><span class="sxs-lookup"><span data-stu-id="8bb41-118">Description</span></span>|<span data-ttu-id="8bb41-119">範例</span><span class="sxs-lookup"><span data-stu-id="8bb41-119">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="8bb41-120">任何包含零個或多個字元的 `string`。</span><span class="sxs-lookup"><span data-stu-id="8bb41-120">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="8bb41-121">`title like '%computer%'`尋找標題中任何位置有`"computer"`單字的所有標題。</span><span class="sxs-lookup"><span data-stu-id="8bb41-121">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="8bb41-122">_ (底線)</span><span class="sxs-lookup"><span data-stu-id="8bb41-122">_ (underscore)</span></span>|<span data-ttu-id="8bb41-123">任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-123">Any single character.</span></span>|<span data-ttu-id="8bb41-124">`firstname like '_ean'`尋找所有四個字母的名字, 其結尾`"ean`為 ", 例如 Dean 或小紅。</span><span class="sxs-lookup"><span data-stu-id="8bb41-124">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="8bb41-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="8bb41-125">[ ]</span></span>|<span data-ttu-id="8bb41-126">在指定範圍 ([a-f]) 或集合 ([abcdef]) 中的任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-126">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="8bb41-127">`lastname like '[C-P]arsen'`尋找結尾為 "arsen" 且開頭為 C 和 P 之間任何單一字元的姓氏, 例如 Carsen 或 Larsen。</span><span class="sxs-lookup"><span data-stu-id="8bb41-127">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="8bb41-128">[^]</span><span class="sxs-lookup"><span data-stu-id="8bb41-128">[^]</span></span>|<span data-ttu-id="8bb41-129">不在指定範圍 ([^a-f]) 或集合 ([^abcdef]) 中的任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-129">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="8bb41-130">`lastname like 'de[^l]%'`尋找所有開頭為 "de" 且不包含 "l" 作為下列字母的姓氏。</span><span class="sxs-lookup"><span data-stu-id="8bb41-130">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8bb41-131">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 運算子和 ESCAPE 子句不可套用到 `System.DateTime` 或 `System.Guid` 值。</span><span class="sxs-lookup"><span data-stu-id="8bb41-131">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="8bb41-132">LIKE 支援 ASCII 模式比對和 Unicode 模式比對。</span><span class="sxs-lookup"><span data-stu-id="8bb41-132">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="8bb41-133">如果所有參數都是 ASCII 字元，便會執行 ASCII 模式比對。</span><span class="sxs-lookup"><span data-stu-id="8bb41-133">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="8bb41-134">如果有任何引數不是 Unicode 資料類型，所有引數都會轉換成 Unicode，然後執行 Unicode 模式比對。</span><span class="sxs-lookup"><span data-stu-id="8bb41-134">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="8bb41-135">使用 Unicode 配合 LIKE 時，尾端空白是有意義的；但是對於非 Unicode，尾端空白就無關重要了。</span><span class="sxs-lookup"><span data-stu-id="8bb41-135">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="8bb41-136">的模式字串語法[!INCLUDE[esql](../../../../../../includes/esql-md.md)]與 transact-sql 相同。</span><span class="sxs-lookup"><span data-stu-id="8bb41-136">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of Transact-SQL.</span></span>  
  
 <span data-ttu-id="8bb41-137">模式可包括一般字元和萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-137">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="8bb41-138">在模式比對期間，一般字元必須與字元 `string` 中所指定的字元完全相符。</span><span class="sxs-lookup"><span data-stu-id="8bb41-138">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="8bb41-139">不過，萬用字元可以符合任意字元字串片段。</span><span class="sxs-lookup"><span data-stu-id="8bb41-139">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="8bb41-140">配合萬用字元使用時，LIKE 運算子會比 = 和 != 字串比較運算子更有彈性。</span><span class="sxs-lookup"><span data-stu-id="8bb41-140">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bb41-141">如果您要針對特定的提供者，可以使用提供者專用的運算式。</span><span class="sxs-lookup"><span data-stu-id="8bb41-141">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="8bb41-142">不過其他提供者可能會以不同方式處理這類建構。</span><span class="sxs-lookup"><span data-stu-id="8bb41-142">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="8bb41-143">SqlServer 支援 [first-last] 和 [^first-last] 模式，前者會在最前與最後範圍之間恰好符合一個字元 (只能有一個字元相符)，後者則是在最前與最後範圍之外恰好符合一個字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-143">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="8bb41-144">逸出字元</span><span class="sxs-lookup"><span data-stu-id="8bb41-144">Escape</span></span>  
 <span data-ttu-id="8bb41-145">使用 ESCAPE 子句可以搜尋包含一或多個先前章節表格中所述特殊萬用字元的字元字串。</span><span class="sxs-lookup"><span data-stu-id="8bb41-145">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="8bb41-146">舉例來講，假設有幾份文件的標題包含常值 "100%"，而您想要搜尋所有這些文件。</span><span class="sxs-lookup"><span data-stu-id="8bb41-146">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="8bb41-147">因為百分比 (%)字元是萬用字元, 您必須使用[!INCLUDE[esql](../../../../../../includes/esql-md.md)] escape 子句來加以轉義, 才能順利執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="8bb41-147">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="8bb41-148">以下就是這項篩選的範例。</span><span class="sxs-lookup"><span data-stu-id="8bb41-148">The following is an example of this filter.</span></span>  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="8bb41-149">在這個搜尋運算式中，緊接在驚嘆號字元 (!) 後面的百分比萬用字元 (%) 會被視為常值，而不是萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-149">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="8bb41-150">除了[!INCLUDE[esql](../../../../../../includes/esql-md.md)]萬用字元和方括弧 (`[ ]`) 字元以外, 您可以使用任何字元做為 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-150">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="8bb41-151">在前一個範例中，驚嘆號 (!) 字元是逸出字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-151">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bb41-152">範例</span><span class="sxs-lookup"><span data-stu-id="8bb41-152">Example</span></span>  
 <span data-ttu-id="8bb41-153">下列兩個[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢使用 LIKE 和 ESCAPE 運算子來判斷特定的字元字串是否符合指定的模式。</span><span class="sxs-lookup"><span data-stu-id="8bb41-153">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="8bb41-154">第一個查詢會搜尋以`Name`字元`Down_`開頭的。</span><span class="sxs-lookup"><span data-stu-id="8bb41-154">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="8bb41-155">這個查詢使用了 ESCAPE 選項，因為底線 (`_`) 是萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8bb41-155">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="8bb41-156">若未指定 ESCAPE 選項, 查詢會搜尋任何`Name`以單字`Down`開頭, 後面接著底線字元以外之任何單一字元的值。</span><span class="sxs-lookup"><span data-stu-id="8bb41-156">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="8bb41-157">這些查詢是以 AdventureWorks Sales Model 為基礎。</span><span class="sxs-lookup"><span data-stu-id="8bb41-157">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8bb41-158">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="8bb41-158">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8bb41-159">[遵循 how to:執行可傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="8bb41-159">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="8bb41-160">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="8bb41-160">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a><span data-ttu-id="8bb41-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bb41-161">See also</span></span>

- [<span data-ttu-id="8bb41-162">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="8bb41-162">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
