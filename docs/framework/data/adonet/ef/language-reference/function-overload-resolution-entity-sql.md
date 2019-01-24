---
title: 函式多載解析 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 9b8e2a4f26c0101141292b768ee5870db78c90b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625168"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="e4c6c-102">函式多載解析 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e4c6c-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="e4c6c-103">本主題描述如何解析 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 函式。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="e4c6c-104">可以定義一個以上的同名函式，只要這些函式具有唯一的簽章即可。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="e4c6c-105">在這種情況下，必須套用下列準則，以判斷哪一個函式是由給定的運算式參考。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="e4c6c-106">這些準則會依序套用。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="e4c6c-107">只套用到單一函式的第一個準則就是被解析的函式。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1.  <span data-ttu-id="e4c6c-108">**參數編號**。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-108">**Parameter number**.</span></span> <span data-ttu-id="e4c6c-109">此函式具有運算式中指定的相同參數數目。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2.  <span data-ttu-id="e4c6c-110">**型別完全相符**。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-110">**Exact match on type**.</span></span> <span data-ttu-id="e4c6c-111">此函式的每一個引數型別都完全符合參數型別，或是為 null 常值。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3.  <span data-ttu-id="e4c6c-112">**符合子型別**。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-112">**Match on subtype**.</span></span> <span data-ttu-id="e4c6c-113">此函式的每一個引數型別都完全符合或是為參數型別的子型別，或者引數為 null 常值。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="e4c6c-114">萬一有幾個函式只有所需的子型別轉換數目不同，則具有最少子型別轉換數目的函式就是被解析的函式。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4.  <span data-ttu-id="e4c6c-115">**符合的子型別或型別提升**。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="e4c6c-116">此函式的每一個引數型別都完全符合或是為參數型別的子型別，或者可以提升為參數型別，或是引數為 null 常值。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="e4c6c-117">同樣地，萬一有幾個函式只有子型別轉換和提升數目不同，則具有最少子型別轉換和提升數目的函式就是被解析的函式。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="e4c6c-118">如果沒有一個準則導致單一函式被選取，表示函式引動過程運算式模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="e4c6c-119">即使可以使用這些規則擷取單一函式，引數仍然可能不符合參數。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="e4c6c-120">在此情況下會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="e4c6c-121">針對使用者定義函式，即使存在更符合使用者定義函式且含簽章的模型定義函式，內嵌查詢函式的定義仍擁有較高的優先順序。</span><span class="sxs-lookup"><span data-stu-id="e4c6c-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c6c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4c6c-122">See also</span></span>
- [<span data-ttu-id="e4c6c-123">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="e4c6c-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e4c6c-124">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="e4c6c-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="e4c6c-125">函式</span><span class="sxs-lookup"><span data-stu-id="e4c6c-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
