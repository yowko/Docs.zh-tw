---
title: 命令樹的形狀
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 9084e2616ac4ea540bdf755afd011d67a5c991fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766032"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="0bac5-102">命令樹的形狀</span><span class="sxs-lookup"><span data-stu-id="0bac5-102">The Shape of the Command Trees</span></span>
<span data-ttu-id="0bac5-103">SQL 產生模組負責根據給定輸入查詢命令樹運算式，產生後端特定的 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="0bac5-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="0bac5-104">本章節將討論查詢命令樹的特性、屬性和結構。</span><span class="sxs-lookup"><span data-stu-id="0bac5-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>  
  
## <a name="query-command-trees-overview"></a><span data-ttu-id="0bac5-105">查詢命令樹概觀</span><span class="sxs-lookup"><span data-stu-id="0bac5-105">Query Command Trees Overview</span></span>  
 <span data-ttu-id="0bac5-106">查詢命令樹是某個查詢的物件模型表示法。</span><span class="sxs-lookup"><span data-stu-id="0bac5-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="0bac5-107">查詢命令樹有兩個用途：</span><span class="sxs-lookup"><span data-stu-id="0bac5-107">Query command trees serve two purposes:</span></span>  
  
-   <span data-ttu-id="0bac5-108">為了表示針對 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 所指定的輸入查詢。</span><span class="sxs-lookup"><span data-stu-id="0bac5-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="0bac5-109">為了表示提供給提供者並針對後端描述查詢的輸出查詢。</span><span class="sxs-lookup"><span data-stu-id="0bac5-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>  
  
 <span data-ttu-id="0bac5-110">查詢命令樹可支援比 SQL:1999 相容的查詢更為豐富的語意，包括使用巢狀集合和型別作業的支援，就像檢查某個實體是否具有特定型別，或者根據型別篩選集合。</span><span class="sxs-lookup"><span data-stu-id="0bac5-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>  
  
 <span data-ttu-id="0bac5-111">DBQueryCommandTree.Query 屬性是描述查詢邏輯之運算式樹狀架構的根。</span><span class="sxs-lookup"><span data-stu-id="0bac5-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="0bac5-112">DBQueryCommandTree.Parameters 屬性包含用於查詢的參數清單。</span><span class="sxs-lookup"><span data-stu-id="0bac5-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="0bac5-113">由 DbExpression 物件所組成的運算式。</span><span class="sxs-lookup"><span data-stu-id="0bac5-113">The expression tree is composed of DbExpression objects.</span></span>  
  
 <span data-ttu-id="0bac5-114">DbExpression 物件代表某些計算。</span><span class="sxs-lookup"><span data-stu-id="0bac5-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="0bac5-115">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會提供幾種運算式來撰寫查詢運算式，包括常數、變數、函式、建構函式，以及標準關係運算子 (如 Filter 和 Join)。</span><span class="sxs-lookup"><span data-stu-id="0bac5-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="0bac5-116">每一個 DbExpression 物件都有 ResultType 屬性，代表該運算式所產生的結果類型。</span><span class="sxs-lookup"><span data-stu-id="0bac5-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="0bac5-117">這個型別會表示為 TypeUsage。</span><span class="sxs-lookup"><span data-stu-id="0bac5-117">This type is expressed as a TypeUsage.</span></span>  
  
## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="0bac5-118">輸出查詢命令樹的形狀</span><span class="sxs-lookup"><span data-stu-id="0bac5-118">Shapes of the Output Query Command Tree</span></span>  
 <span data-ttu-id="0bac5-119">輸出查詢命令樹緊密地代表關聯式 (SQL) 查詢，而且與查詢命令樹所套用的規則相較之下，前者會遵守更為嚴格的規則。</span><span class="sxs-lookup"><span data-stu-id="0bac5-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="0bac5-120">這些通常包含可輕鬆轉譯為 SQL 的建構。</span><span class="sxs-lookup"><span data-stu-id="0bac5-120">They typically contain constructs that are easily translated to SQL.</span></span>  
  
 <span data-ttu-id="0bac5-121">輸入命令樹會針對概念模型來表示，概念模型可支援導覽屬性、多個實體之間的關聯及繼承。</span><span class="sxs-lookup"><span data-stu-id="0bac5-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="0bac5-122">輸出命令樹會針對儲存體模型來表示。</span><span class="sxs-lookup"><span data-stu-id="0bac5-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="0bac5-123">輸入命令樹可讓您投射巢狀集合，但輸出命令樹則不行。</span><span class="sxs-lookup"><span data-stu-id="0bac5-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>  
  
 <span data-ttu-id="0bac5-124">輸出查詢命令樹是使用可用的 DbExpression 物件子集所建置，而且即使是該子集中的某些運算式也是有使用上的限制。</span><span class="sxs-lookup"><span data-stu-id="0bac5-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>  
  
 <span data-ttu-id="0bac5-125">型別作業 (就像檢查給定運算式是否具有特定型別，或是根據型別篩選集合) 不會出現在輸出命令樹中。</span><span class="sxs-lookup"><span data-stu-id="0bac5-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>  
  
 <span data-ttu-id="0bac5-126">在輸出命令樹中，只有傳回布林值的運算式會用於投射，而且只適用於需要述詞 (如 filter 或 case 陳述式) 之運算式中的述詞。</span><span class="sxs-lookup"><span data-stu-id="0bac5-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>  
  
 <span data-ttu-id="0bac5-127">輸出查詢命令樹的根為 DbProjectExpression 物件。</span><span class="sxs-lookup"><span data-stu-id="0bac5-127">The root of an output query command trees is a DbProjectExpression object.</span></span>  
  
### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="0bac5-128">輸出查詢命令樹中未出現運算式型別</span><span class="sxs-lookup"><span data-stu-id="0bac5-128">Expression Types Not Present in Output Query Command Trees</span></span>  
 <span data-ttu-id="0bac5-129">下列運算式型別在輸出查詢命令樹中無效，而且不需要由提供者來處理：</span><span class="sxs-lookup"><span data-stu-id="0bac5-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>  
  
 <span data-ttu-id="0bac5-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-130">DbDerefExpression</span></span>  
  
 <span data-ttu-id="0bac5-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-131">DbEntityRefExpression</span></span>  
  
 <span data-ttu-id="0bac5-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-132">DbRefKeyExpression</span></span>  
  
 <span data-ttu-id="0bac5-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-133">DbIsOfExpression</span></span>  
  
 <span data-ttu-id="0bac5-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-134">DbOfTypeExpression</span></span>  
  
 <span data-ttu-id="0bac5-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-135">DbRefExpression</span></span>  
  
 <span data-ttu-id="0bac5-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-136">DbRelationshipNavigationExpression</span></span>  
  
 <span data-ttu-id="0bac5-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-137">DbTreatExpression</span></span>  
  
### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="0bac5-138">運算式限制和備註</span><span class="sxs-lookup"><span data-stu-id="0bac5-138">Expression Restrictions and Notes</span></span>  
 <span data-ttu-id="0bac5-139">許多運算式在輸出查詢命令樹中，只能以限制的方式來使用：</span><span class="sxs-lookup"><span data-stu-id="0bac5-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>  
  
#### <a name="dbfunctionexpression"></a><span data-ttu-id="0bac5-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-140">DbFunctionExpression</span></span>  
 <span data-ttu-id="0bac5-141">下列是可以傳遞的函式型別：</span><span class="sxs-lookup"><span data-stu-id="0bac5-141">The following function types can be passed:</span></span>  
  
-   <span data-ttu-id="0bac5-142">Edm 命名空間所辨識的標準函式。</span><span class="sxs-lookup"><span data-stu-id="0bac5-142">Canonical functions that are recognized by the Edm namespace.</span></span>  
  
-   <span data-ttu-id="0bac5-143">BuiltInAttribute 所辨識的內建 (存放區) 函式。</span><span class="sxs-lookup"><span data-stu-id="0bac5-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>  
  
-   <span data-ttu-id="0bac5-144">使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="0bac5-144">User-defined functions.</span></span>  
  
 <span data-ttu-id="0bac5-145">標準函式 (請參閱[標準函式](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)如需詳細資訊) 指定為一部分[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]，並提供者應該提供這些規格為基礎的標準函式的實作。</span><span class="sxs-lookup"><span data-stu-id="0bac5-145">Canonical functions (see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="0bac5-146">存放區函式是根據對應之提供者資訊清單中的規格。</span><span class="sxs-lookup"><span data-stu-id="0bac5-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="0bac5-147">使用者定義函式是根據 SSDL 中的規格。</span><span class="sxs-lookup"><span data-stu-id="0bac5-147">User defined functions are based on specifications in the SSDL.</span></span>  
  
 <span data-ttu-id="0bac5-148">此外，具有 NiladicFunction 屬性的函式沒有任何引數，而且轉譯時結尾不應該有括號。</span><span class="sxs-lookup"><span data-stu-id="0bac5-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="0bac5-149">也就是為 *\<functionName >* 而不是 *\<functionName > （)*。</span><span class="sxs-lookup"><span data-stu-id="0bac5-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>  
  
#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="0bac5-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-150">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="0bac5-151">DbNewInstanceExpression 只能發生在下列兩個案例中：</span><span class="sxs-lookup"><span data-stu-id="0bac5-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>  
  
-   <span data-ttu-id="0bac5-152">當做 DbProjectExpression 的 Projection 屬性。</span><span class="sxs-lookup"><span data-stu-id="0bac5-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="0bac5-153">當依照這類情況使用時，要遵守下列限制：</span><span class="sxs-lookup"><span data-stu-id="0bac5-153">When used as such the following restrictions apply:</span></span>  
  
    -   <span data-ttu-id="0bac5-154">結果型別必須是資料列型別。</span><span class="sxs-lookup"><span data-stu-id="0bac5-154">The result type must be a row type.</span></span>  
  
    -   <span data-ttu-id="0bac5-155">它的每一個引數都是一個運算式，可產生具有基本型別的結果。</span><span class="sxs-lookup"><span data-stu-id="0bac5-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="0bac5-156">一般來說，每一個引數都是純量運算式，例如透過 DbVariableReferenceExpression 的 PropertyExpression、函式引動過程，或是透過 DbVariableReferenceExpression 或函式引動過程之 DbPropertyExpression 的算術運算。</span><span class="sxs-lookup"><span data-stu-id="0bac5-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="0bac5-157">但是，代表純量子查詢的運算式也可以出現在 DbNewInstanceExpression 的引數清單中。</span><span class="sxs-lookup"><span data-stu-id="0bac5-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="0bac5-158">代表純量子查詢的運算式是代表子查詢的一種運算式樹狀架構，可恰好傳回基本型別的一個資料列和一個資料行，而且包含 DbElementExperession 物件根。</span><span class="sxs-lookup"><span data-stu-id="0bac5-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExperession object root</span></span>  
  
-   <span data-ttu-id="0bac5-159">有了集合傳回型別，就可以定義當做引數提供之運算式的新集合。</span><span class="sxs-lookup"><span data-stu-id="0bac5-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>  
  
#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="0bac5-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-160">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="0bac5-161">DbVariableReferenceExpression 必須是 DbPropertyExpression 節點的子系。</span><span class="sxs-lookup"><span data-stu-id="0bac5-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>  
  
#### <a name="dbgroupbyexpression"></a><span data-ttu-id="0bac5-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-162">DbGroupByExpression</span></span>  
 <span data-ttu-id="0bac5-163">DbGroupByExpression 的 Aggregates 屬性只能擁有 DbFunctionAggregate 型別的項目。</span><span class="sxs-lookup"><span data-stu-id="0bac5-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="0bac5-164">沒有其他任何彙總型別。</span><span class="sxs-lookup"><span data-stu-id="0bac5-164">There are no other aggregate types.</span></span>  
  
#### <a name="dblimitexpression"></a><span data-ttu-id="0bac5-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-165">DbLimitExpression</span></span>  
 <span data-ttu-id="0bac5-166">屬性限制只能是 DbConstantExpression 或 DbParameterReferenceExpression。</span><span class="sxs-lookup"><span data-stu-id="0bac5-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="0bac5-167">此外，WithTies 屬性在 .NET Framework 3.5 版中一定是 false。</span><span class="sxs-lookup"><span data-stu-id="0bac5-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>  
  
#### <a name="dbscanexpression"></a><span data-ttu-id="0bac5-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="0bac5-168">DbScanExpression</span></span>  
 <span data-ttu-id="0bac5-169">當用於輸出命令樹時，DbScanExpression 會有效地代表對資料表、檢閱表或存放區查詢的掃描 (以 EnitySetBase::Target 表示)。</span><span class="sxs-lookup"><span data-stu-id="0bac5-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EnitySetBase::Target.</span></span>  
  
 <span data-ttu-id="0bac5-170">如果中繼資料屬性"Defining Query"的目標是不是 null，它會代表查詢，查詢文字會在提供存放結構定義中所指定的提供者特定的語言 （或方言） 中的中繼資料屬性。</span><span class="sxs-lookup"><span data-stu-id="0bac5-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>  
  
 <span data-ttu-id="0bac5-171">否則，目標會代表資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="0bac5-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="0bac5-172">其結構描述前置詞不是位於"Schema"中繼資料屬性，如果不是 null，就是實體容器名稱。</span><span class="sxs-lookup"><span data-stu-id="0bac5-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="0bac5-173">資料表或檢視表名稱會是"Table"中繼資料屬性，如果不是 null，否則為 Name 屬性的實體集基底。</span><span class="sxs-lookup"><span data-stu-id="0bac5-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>  
  
 <span data-ttu-id="0bac5-174">所有的這些屬性都來自於存放結構定義檔案 (SSDL) 中對應 EntitySet 的定義。</span><span class="sxs-lookup"><span data-stu-id="0bac5-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>  
  
### <a name="using-primitive-types"></a><span data-ttu-id="0bac5-175">使用基本型別</span><span class="sxs-lookup"><span data-stu-id="0bac5-175">Using Primitive Types</span></span>  
 <span data-ttu-id="0bac5-176">在輸出命令樹中參考基本型別時，通常會在概念模型的基本型別中參考這些型別。</span><span class="sxs-lookup"><span data-stu-id="0bac5-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="0bac5-177">但是對於某些運算式而言，提供者需要對應的存放區基本型別。</span><span class="sxs-lookup"><span data-stu-id="0bac5-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="0bac5-178">這類運算式的範例包括 DbCastExpression，也可能包括 DbNullExpression (如果提供者需要將 null 轉型為對應的型別)。</span><span class="sxs-lookup"><span data-stu-id="0bac5-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="0bac5-179">在這些情況下，提供者應該根據基本型別種類和它的 Facet，執行與提供者型別的對應。</span><span class="sxs-lookup"><span data-stu-id="0bac5-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bac5-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bac5-180">See Also</span></span>  
 [<span data-ttu-id="0bac5-181">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="0bac5-181">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
