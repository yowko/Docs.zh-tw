---
title: 識別項 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 55b9ac101c7849c5b348ba8e48c695c0fa328105
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765876"
---
# <a name="identifiers-entity-sql"></a><span data-ttu-id="4fc73-102">識別項 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4fc73-102">Identifiers (Entity SQL)</span></span>
<span data-ttu-id="4fc73-103">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中使用識別項表示查詢運算式別名、變數參考、物件的屬性、函式等。</span><span class="sxs-lookup"><span data-stu-id="4fc73-103">Identifiers are used in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to represent query expression aliases, variable references, properties of objects, functions, and so on.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4fc73-104"> 提供兩種類型的識別項： 簡單識別項和引號識別項。</span><span class="sxs-lookup"><span data-stu-id="4fc73-104"> provides two kinds of identifiers: simple identifiers and quoted identifiers.</span></span>  
  
## <a name="simple-identifiers"></a><span data-ttu-id="4fc73-105">簡單識別項</span><span class="sxs-lookup"><span data-stu-id="4fc73-105">Simple Identifiers</span></span>  
 <span data-ttu-id="4fc73-106">簡單識別項中的[!INCLUDE[esql](../../../../../../includes/esql-md.md)]是一連串的英數字元和底線字元。</span><span class="sxs-lookup"><span data-stu-id="4fc73-106">A simple identifier in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is a sequence of alphanumeric and underscore characters.</span></span> <span data-ttu-id="4fc73-107">識別項的第一個字元必須是字母字元 (a-z 或 A-Z)。</span><span class="sxs-lookup"><span data-stu-id="4fc73-107">The first character of the identifier must be an alphabetical character (a-z or A-Z).</span></span>  
  
## <a name="quoted-identifiers"></a><span data-ttu-id="4fc73-108">引號識別項</span><span class="sxs-lookup"><span data-stu-id="4fc73-108">Quoted Identifiers</span></span>  
 <span data-ttu-id="4fc73-109">引號識別項是以方括弧 ([]) 括住的任何字元序列。</span><span class="sxs-lookup"><span data-stu-id="4fc73-109">A quoted identifier is any sequence of characters enclosed in square brackets ([]).</span></span> <span data-ttu-id="4fc73-110">引號識別項可讓您使用在識別項中無效的字元來指定識別項。</span><span class="sxs-lookup"><span data-stu-id="4fc73-110">Quoted identifiers let you specify identifiers with characters that are not valid in identifiers.</span></span> <span data-ttu-id="4fc73-111">方括弧內的所有字元都會變成識別項的一部分，包括所有空白字元。</span><span class="sxs-lookup"><span data-stu-id="4fc73-111">All characters between the square brackets become part of the identifier, including all whitespace.</span></span>  
  
 <span data-ttu-id="4fc73-112">引號識別項不能包含下列字元：</span><span class="sxs-lookup"><span data-stu-id="4fc73-112">A quoted identifier cannot include the following characters:</span></span>  
  
-   <span data-ttu-id="4fc73-113">新行 (Newline)。</span><span class="sxs-lookup"><span data-stu-id="4fc73-113">Newline.</span></span>  
  
-   <span data-ttu-id="4fc73-114">歸位字元 (Carriage Return)。</span><span class="sxs-lookup"><span data-stu-id="4fc73-114">Carriage returns.</span></span>  
  
-   <span data-ttu-id="4fc73-115">定位點。</span><span class="sxs-lookup"><span data-stu-id="4fc73-115">Tabs.</span></span>  
  
-   <span data-ttu-id="4fc73-116">退格鍵。</span><span class="sxs-lookup"><span data-stu-id="4fc73-116">Backspace.</span></span>  
  
-   <span data-ttu-id="4fc73-117">其他方括弧 (也就是方括弧內描寫識別項的方括弧)。</span><span class="sxs-lookup"><span data-stu-id="4fc73-117">Additional square brackets (that is, square brackets within the square brackets that delineate the identifier).</span></span>  
  
 <span data-ttu-id="4fc73-118">引號識別項可包含 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="4fc73-118">A quoted-identifier can include Unicode characters.</span></span>  
  
 <span data-ttu-id="4fc73-119">引號識別項可讓您建立在識別項中無效的屬性名稱字元，如下列範例所述：</span><span class="sxs-lookup"><span data-stu-id="4fc73-119">Quoted identifiers enable you to create property name characters that are not valid in identifiers, as illustrated in the following example:</span></span>  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 <span data-ttu-id="4fc73-120">您也可以使用引號識別項來指定 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 保留關鍵字的識別項。</span><span class="sxs-lookup"><span data-stu-id="4fc73-120">You can also use quoted identifiers to specify an identifier that is a reserved keyword of [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="4fc73-121">例如，如果型別 `Email` 具有名為 "From" 的屬性，您就可以使用方括弧釐清 "From" 屬性與保留的關鍵字 FROM。</span><span class="sxs-lookup"><span data-stu-id="4fc73-121">For example, if the type `Email` has a property named "From", you can disambiguate it from the reserved keyword FROM by using square brackets, as follows:</span></span>  
  
 `SELECT e.[From] FROM emails AS e`  
  
 <span data-ttu-id="4fc73-122">您可以在點 (.) 運算子的右邊使用引號識別項 (Quoted Identifier)</span><span class="sxs-lookup"><span data-stu-id="4fc73-122">You can use a quoted identifier on the right side of a dot (.) operator.</span></span>  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 <span data-ttu-id="4fc73-123">若要在識別項中使用方括弧，必須加上額外的方括弧。</span><span class="sxs-lookup"><span data-stu-id="4fc73-123">To use the square bracket in an identifier, add an extra square bracket.</span></span> <span data-ttu-id="4fc73-124">下列範例中的 "`abc]`" 為識別項：</span><span class="sxs-lookup"><span data-stu-id="4fc73-124">In the following example "`abc]`" is the identifier:</span></span>  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 <span data-ttu-id="4fc73-125">引號識別項的比較語意，請參閱[輸入字元集](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="4fc73-125">For quoted identifier comparison semantics, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="aliasing-rules"></a><span data-ttu-id="4fc73-126">別名規則</span><span class="sxs-lookup"><span data-stu-id="4fc73-126">Aliasing Rules</span></span>  
 <span data-ttu-id="4fc73-127">我們建議您指定的別名[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢每次需要包括下列[!INCLUDE[esql](../../../../../../includes/esql-md.md)]建構：</span><span class="sxs-lookup"><span data-stu-id="4fc73-127">We recommend specifying aliases in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries whenever needed, including the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs:</span></span>  
  
-   <span data-ttu-id="4fc73-128">資料列建構函式 (Constructor) 的欄位。</span><span class="sxs-lookup"><span data-stu-id="4fc73-128">Fields of a row constructor.</span></span>  
  
-   <span data-ttu-id="4fc73-129">查詢運算式之 FROM 子句中的項目。</span><span class="sxs-lookup"><span data-stu-id="4fc73-129">Items in the FROM clause of a query expression.</span></span>  
  
-   <span data-ttu-id="4fc73-130">查詢運算式之 SELECT 子句中的項目。</span><span class="sxs-lookup"><span data-stu-id="4fc73-130">Items in the SELECT clause of a query expression.</span></span>  
  
-   <span data-ttu-id="4fc73-131">查詢運算式之 GROUP BY 子句中的項目。</span><span class="sxs-lookup"><span data-stu-id="4fc73-131">Items in the GROUP BY clause of a query expression.</span></span>  
  
### <a name="valid-aliases"></a><span data-ttu-id="4fc73-132">有效的別名</span><span class="sxs-lookup"><span data-stu-id="4fc73-132">Valid Aliases</span></span>  
 <span data-ttu-id="4fc73-133">中有效的別名[!INCLUDE[esql](../../../../../../includes/esql-md.md)]任何簡單識別項或引號識別項。</span><span class="sxs-lookup"><span data-stu-id="4fc73-133">Valid aliases in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are any simple identifier or quoted identifier.</span></span>  
  
### <a name="alias-generation"></a><span data-ttu-id="4fc73-134">別名產生</span><span class="sxs-lookup"><span data-stu-id="4fc73-134">Alias Generation</span></span>  
 <span data-ttu-id="4fc73-135">如果未指定別名中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢運算式，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]嘗試產生根據以下簡單規則的別名：</span><span class="sxs-lookup"><span data-stu-id="4fc73-135">If no alias is specified in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the following simple rules:</span></span>  
  
-   <span data-ttu-id="4fc73-136">如果查詢運算式 (未指定別名) 是簡單識別項或引號識別項，會使用該識別項當做別名。</span><span class="sxs-lookup"><span data-stu-id="4fc73-136">If the query expression (for which the alias is unspecified) is a simple or quoted identifier, that identifier is used as the alias.</span></span> <span data-ttu-id="4fc73-137">例如，`ROW(a, [b])` 會成為 `ROW(a AS a, [b] AS [b])`。</span><span class="sxs-lookup"><span data-stu-id="4fc73-137">For example, `ROW(a, [b])` becomes `ROW(a AS a, [b] AS [b])`.</span></span>  
  
-   <span data-ttu-id="4fc73-138">如果查詢運算式是比較複雜的運算式，但是該查詢運算式的最後一個元件是簡單識別項，則會使用該識別項當做別名。</span><span class="sxs-lookup"><span data-stu-id="4fc73-138">If the query expression is a more complex expression, but the last component of that query expression is a simple identifier, then that identifier is used as the alias.</span></span> <span data-ttu-id="4fc73-139">例如，`ROW(a.a1, b.[b1])` 會成為 `ROW(a.a1 AS a1, b.[b1] AS [b1])`。</span><span class="sxs-lookup"><span data-stu-id="4fc73-139">For example, `ROW(a.a1, b.[b1])` becomes `ROW(a.a1 AS a1, b.[b1] AS [b1])`.</span></span>  
  
 <span data-ttu-id="4fc73-140">如果您想要在稍後使用別名名稱，建議您不要使用隱含別名。</span><span class="sxs-lookup"><span data-stu-id="4fc73-140">We recommend that you do not use implicit aliasing if you want to use the alias name later.</span></span> <span data-ttu-id="4fc73-141">任何時候發生別名 (隱含或明確) 衝突或是在相同的範圍內重複別名時，都會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="4fc73-141">Anytime aliases (implicit or explicit) conflict or are repeated in the same scope, there will be a compile error.</span></span> <span data-ttu-id="4fc73-142">即使有同名的明確或隱含別名，隱含別名還是會通過編譯程序。</span><span class="sxs-lookup"><span data-stu-id="4fc73-142">An implicit alias will pass compilation even if there is an explicit or implicit alias of the same name.</span></span>  
  
 <span data-ttu-id="4fc73-143">隱含別名會根據使用者輸入自動產生。</span><span class="sxs-lookup"><span data-stu-id="4fc73-143">Implicit aliases are autogenerated based on user input.</span></span> <span data-ttu-id="4fc73-144">例如，下列這一行程式碼將會產生 NAME 當做這兩個資料行的別名，因此會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="4fc73-144">For example, the following line of code will generate NAME as an alias for both columns and therefore will conflict.</span></span>  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 <span data-ttu-id="4fc73-145">下列這一行程式碼 (使用明確別名) 也會失敗。</span><span class="sxs-lookup"><span data-stu-id="4fc73-145">The following line of code, which uses explicit aliases, will also fail.</span></span> <span data-ttu-id="4fc73-146">但是，閱讀程式碼就會更清楚看到失敗。</span><span class="sxs-lookup"><span data-stu-id="4fc73-146">However, the failure will be more apparent by reading the code.</span></span>  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a><span data-ttu-id="4fc73-147">範圍規則</span><span class="sxs-lookup"><span data-stu-id="4fc73-147">Scoping Rules</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4fc73-148"> 定義範圍規則可判斷當特定變數中會顯示查詢語言。</span><span class="sxs-lookup"><span data-stu-id="4fc73-148"> defines scoping rules that determine when particular variables are visible in the query language.</span></span> <span data-ttu-id="4fc73-149">某些運算式或陳述式會導入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-149">Some expressions or statements introduce new names.</span></span> <span data-ttu-id="4fc73-150">範圍規則可判斷哪裡可以使用這些名稱，以及當新的宣告與另一個宣告同名時，要在何時及何處隱藏它的前置項目。</span><span class="sxs-lookup"><span data-stu-id="4fc73-150">The scoping rules determine where those names can be used, and when or where a new declaration with the same name as another can hide its predecessor.</span></span>  
  
 <span data-ttu-id="4fc73-151">當名稱定義在[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢，就可以說它們定義在範圍內。</span><span class="sxs-lookup"><span data-stu-id="4fc73-151">When names are defined in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, they are said to be defined within a scope.</span></span> <span data-ttu-id="4fc73-152">範圍涵蓋查詢的整個區域。</span><span class="sxs-lookup"><span data-stu-id="4fc73-152">A scope covers an entire region of the query.</span></span> <span data-ttu-id="4fc73-153">某個範圍內的所有運算式或名稱參考都可以看到該範圍內定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-153">All expressions or name references within a certain scope can see names that are defined within that scope.</span></span> <span data-ttu-id="4fc73-154">在範圍開始前及結束後，無法參考此範圍內所定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-154">Before a scope begins and after it ends, names that are defined within the scope cannot be referenced.</span></span>  
  
 <span data-ttu-id="4fc73-155">範圍可以是巢狀的。</span><span class="sxs-lookup"><span data-stu-id="4fc73-155">Scopes can be nested.</span></span> <span data-ttu-id="4fc73-156">部分[!INCLUDE[esql](../../../../../../includes/esql-md.md)]導入新的範圍涵蓋整個區域，而且這些區域可以包含其他[!INCLUDE[esql](../../../../../../includes/esql-md.md)]也導入範圍的運算式。</span><span class="sxs-lookup"><span data-stu-id="4fc73-156">Parts of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduce new scopes that cover entire regions, and these regions can contain other [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that also introduce scopes.</span></span> <span data-ttu-id="4fc73-157">當範圍是巢狀時，可以參考最內部範圍 (包含參考) 內定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-157">When scopes are nested, references can be made to names that are defined in the innermost scope, which contains the reference.</span></span> <span data-ttu-id="4fc73-158">也可以參考任何外部範圍內定義的任何名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-158">References can also be made to any names that are defined in any outer scopes.</span></span> <span data-ttu-id="4fc73-159">相同範圍內定義的任何兩個範圍都視為同層級 (Sibling) 範圍。</span><span class="sxs-lookup"><span data-stu-id="4fc73-159">Any two scopes defined within the same scope are considered sibling scopes.</span></span> <span data-ttu-id="4fc73-160">無法參考同層級範圍內定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-160">References cannot be made to names that are defined within sibling scopes.</span></span>  
  
 <span data-ttu-id="4fc73-161">如果內部範圍內宣告的名稱符合外部範圍內宣告的名稱，則內部範圍中或是該範圍內宣告的範圍中的參考只會參考新宣告的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-161">If a name declared in an inner scope matches a name declared in an outer scope, references within the inner scope or within scopes declared within that scope refer only to the newly declared name.</span></span> <span data-ttu-id="4fc73-162">外部範圍中的名稱則會隱藏。</span><span class="sxs-lookup"><span data-stu-id="4fc73-162">The name in the outer scope is hidden.</span></span>  
  
 <span data-ttu-id="4fc73-163">即使是在相同的範圍中，也一定要在定義名稱之後才可以參考。</span><span class="sxs-lookup"><span data-stu-id="4fc73-163">Even within the same scope, names cannot be referenced before they are defined.</span></span>  
  
 <span data-ttu-id="4fc73-164">全域名稱可以當做執行環境的一部分存在。</span><span class="sxs-lookup"><span data-stu-id="4fc73-164">Global names can exist as part of the execution environment.</span></span> <span data-ttu-id="4fc73-165">這可包括持續性集合或環境變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-165">This can include names of persistent collections or environment variables.</span></span> <span data-ttu-id="4fc73-166">如果希望名稱是全域名稱，必須在最外層範圍宣告它。</span><span class="sxs-lookup"><span data-stu-id="4fc73-166">For a name to be global, it must be declared in the outermost scope.</span></span>  
  
 <span data-ttu-id="4fc73-167">參數不在範圍內。</span><span class="sxs-lookup"><span data-stu-id="4fc73-167">Parameters are not in a scope.</span></span> <span data-ttu-id="4fc73-168">因為參數的參考包含特殊語法，所以參數的名稱永遠都不會與查詢中的其他名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="4fc73-168">Because references to parameters include special syntax, names of parameters will never collide with other names in the query.</span></span>  
  
### <a name="query-expressions"></a><span data-ttu-id="4fc73-169">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="4fc73-169">Query Expressions</span></span>  
 <span data-ttu-id="4fc73-170">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢運算式會導入新的範圍。</span><span class="sxs-lookup"><span data-stu-id="4fc73-170">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query expression introduces a new scope.</span></span> <span data-ttu-id="4fc73-171">FROM 子句中定義的名稱會導入來源範圍內 (根據外觀從左到右)。</span><span class="sxs-lookup"><span data-stu-id="4fc73-171">Names that are defined in the FROM clause are introduced into the from scope in order of appearance, left to right.</span></span> <span data-ttu-id="4fc73-172">在聯結清單中，運算式可以參考之前定義在清單中的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-172">In the join list, expressions can refer to names that were defined earlier in the list.</span></span> <span data-ttu-id="4fc73-173">FROM 子句中識別之項目的公用屬性 (欄位等等) 會加入來源範圍。</span><span class="sxs-lookup"><span data-stu-id="4fc73-173">Public properties (fields and so on) of elements identified in the FROM clause are not added to the from-scope.</span></span> <span data-ttu-id="4fc73-174">這些屬性必須由別名限定的名稱所參考。</span><span class="sxs-lookup"><span data-stu-id="4fc73-174">They must be always referenced by the alias-qualified name.</span></span> <span data-ttu-id="4fc73-175">一般來說，SELECT 運算式的所有部分都視為在來源範圍中。</span><span class="sxs-lookup"><span data-stu-id="4fc73-175">Typically, all parts of the SELECT expression are considered within the from-scope.</span></span>  
  
 <span data-ttu-id="4fc73-176">GROUP BY 子句也會導入新的同層級範圍。</span><span class="sxs-lookup"><span data-stu-id="4fc73-176">The GROUP BY clause also introduces a new sibling scope.</span></span> <span data-ttu-id="4fc73-177">每一個群組都可以有一個群組名稱來參考該群組內的項目集合。</span><span class="sxs-lookup"><span data-stu-id="4fc73-177">Each group can have a group name that refers to the collection of elements in the group.</span></span> <span data-ttu-id="4fc73-178">每一個群組運算式也都會將新的名稱導入群組範圍。</span><span class="sxs-lookup"><span data-stu-id="4fc73-178">Each grouping expression will also introduce a new name into the group-scope.</span></span> <span data-ttu-id="4fc73-179">另外，巢狀彙總 (或具名群組) 也會加入此範圍。</span><span class="sxs-lookup"><span data-stu-id="4fc73-179">Additionally, the nest aggregate (or the named group) is also added to the scope.</span></span> <span data-ttu-id="4fc73-180">群組運算式本身是在來源範圍中。</span><span class="sxs-lookup"><span data-stu-id="4fc73-180">The grouping expressions themselves are within the from-scope.</span></span> <span data-ttu-id="4fc73-181">但是，當使用 GROUP BY 子句時，SELECT 清單 (投影)、HAVING 子句和 ORDER BY 子句都會被視為在群組範圍內，而不在來源範圍內。</span><span class="sxs-lookup"><span data-stu-id="4fc73-181">However, when a GROUP BY clause is used, the select-list (projection), HAVING clause, and ORDER BY clause are considered to be within the group-scope, and not the from-scope.</span></span> <span data-ttu-id="4fc73-182">彙總會收到特殊的對待，如同下列項目符號清單內所述。</span><span class="sxs-lookup"><span data-stu-id="4fc73-182">Aggregates receive special treatment, as described in the following bulleted list.</span></span>  
  
 <span data-ttu-id="4fc73-183">下列是有關範圍的一些其他注意事項：</span><span class="sxs-lookup"><span data-stu-id="4fc73-183">The following are additional notes about scopes:</span></span>  
  
-   <span data-ttu-id="4fc73-184">SELECT 清單可以將新的名稱依序導入此範圍。</span><span class="sxs-lookup"><span data-stu-id="4fc73-184">The select-list can introduce new names into the scope, in order.</span></span> <span data-ttu-id="4fc73-185">右邊的投影運算式可能會參考左邊投影的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc73-185">Projection expressions to the right might refer to names projected on the left.</span></span>  
  
-   <span data-ttu-id="4fc73-186">ORDER BY 子句可參考 SELECT 清單中指定的名稱 (別名)。</span><span class="sxs-lookup"><span data-stu-id="4fc73-186">The ORDER BY clause can refer to names (aliases) specified in the select list.</span></span>  
  
-   <span data-ttu-id="4fc73-187">SELECT 運算式內子句的評估順序會決定名稱導入範圍中的順序。</span><span class="sxs-lookup"><span data-stu-id="4fc73-187">The order of evaluation of clauses within the SELECT expression determines the order that names are introduced into the scope.</span></span> <span data-ttu-id="4fc73-188">FROM 子句會先評估，接著是 WHERE 子句、GROUP BY 子句、HAVING 子句、SELECT 子句，最後是 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="4fc73-188">The FROM clause is evaluated first, followed by the WHERE clause, GROUP BY clause, HAVING clause, SELECT clause, and finally the ORDER BY clause.</span></span>  
  
### <a name="aggregate-handling"></a><span data-ttu-id="4fc73-189">彙總處理</span><span class="sxs-lookup"><span data-stu-id="4fc73-189">Aggregate Handling</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4fc73-190"> 支援兩種形式的彙總： 以集合為基礎的彙總以及以群組為基礎的彙總。</span><span class="sxs-lookup"><span data-stu-id="4fc73-190"> supports two forms of aggregates: collection-based aggregates and group-based aggregates.</span></span> <span data-ttu-id="4fc73-191">以集合為基礎的彙總是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中偏好的建構，以群組為基礎的彙總則是為了與 SQL 相容而支援。</span><span class="sxs-lookup"><span data-stu-id="4fc73-191">Collection-based aggregates are the preferred construct in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], and group-based aggregates are supported for SQL compatibility.</span></span>  
  
 <span data-ttu-id="4fc73-192">當解析彙總，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]先嘗試將它視為以集合為基礎的彙總。</span><span class="sxs-lookup"><span data-stu-id="4fc73-192">When resolving an aggregate, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] first tries to treat it as a collection-based aggregate.</span></span> <span data-ttu-id="4fc73-193">如果失敗，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]將彙總輸入轉換成巢狀彙總的參考，並嘗試解析這個新的運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4fc73-193">If that fails, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transforms the aggregate input into a reference to the nest aggregate and tries to resolve this new expression, as illustrated in the following example.</span></span>  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a><span data-ttu-id="4fc73-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fc73-194">See Also</span></span>  
 [<span data-ttu-id="4fc73-195">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="4fc73-195">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="4fc73-196">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="4fc73-196">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="4fc73-197">輸入字元集</span><span class="sxs-lookup"><span data-stu-id="4fc73-197">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)
