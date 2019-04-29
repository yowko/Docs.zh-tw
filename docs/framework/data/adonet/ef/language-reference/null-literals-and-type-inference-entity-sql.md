---
title: Null 常值和類型推斷 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 22b548f2fc889b20f76a41001438f75c25f99c00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760398"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="a177d-102">Null 常值和類型推斷 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a177d-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="a177d-103">Null 常值與 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 型別系統中的任何型別都相容。</span><span class="sxs-lookup"><span data-stu-id="a177d-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="a177d-104">不過，為了正確推斷 null 常值的型別[!INCLUDE[esql](../../../../../../includes/esql-md.md)]強加特定條件約束可以使用 null 常值的地方。</span><span class="sxs-lookup"><span data-stu-id="a177d-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="a177d-105">具型別的 Null</span><span class="sxs-lookup"><span data-stu-id="a177d-105">Typed Nulls</span></span>  
 <span data-ttu-id="a177d-106">具型別的 Null 可以在任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="a177d-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="a177d-107">具型別的 Null 不需要型別推斷，因為該型別是已知的。</span><span class="sxs-lookup"><span data-stu-id="a177d-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="a177d-108">例如，您可以使用下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 建構來建構 Int16 型別的 Null：</span><span class="sxs-lookup"><span data-stu-id="a177d-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="a177d-109">自由浮動 Null 常值</span><span class="sxs-lookup"><span data-stu-id="a177d-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="a177d-110">自由浮動 Null 常值可以在以下內容中使用：</span><span class="sxs-lookup"><span data-stu-id="a177d-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="a177d-111">當做 CAST 或 TREAT 運算式的引數。</span><span class="sxs-lookup"><span data-stu-id="a177d-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="a177d-112">建議使用這個方式來產生具型別的 Null 運算式。</span><span class="sxs-lookup"><span data-stu-id="a177d-112">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="a177d-113">當做方法或函式的引數。</span><span class="sxs-lookup"><span data-stu-id="a177d-113">As an argument to a method or a function.</span></span> <span data-ttu-id="a177d-114">套用標準多載規則。</span><span class="sxs-lookup"><span data-stu-id="a177d-114">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="a177d-115">當做算術運算式的其中一個引數，例如 +、- 或 /。</span><span class="sxs-lookup"><span data-stu-id="a177d-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="a177d-116">其他引數不能是 Null 常值，否則無法進行型別推斷。</span><span class="sxs-lookup"><span data-stu-id="a177d-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="a177d-117">當做邏輯運算式的任何引數 (AND、OR 或 NOT)。</span><span class="sxs-lookup"><span data-stu-id="a177d-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="a177d-118">已知所有引數都具有 Boolean 型別。</span><span class="sxs-lookup"><span data-stu-id="a177d-118">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="a177d-119">當做 IS NULL 或 IS NOT NULL 運算式的引數。</span><span class="sxs-lookup"><span data-stu-id="a177d-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="a177d-120">當做 LIKE 運算式的其中一個或多個引數。</span><span class="sxs-lookup"><span data-stu-id="a177d-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="a177d-121">所有引數都必須是字串。</span><span class="sxs-lookup"><span data-stu-id="a177d-121">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="a177d-122">當做具名型別建構函式 (Constructor) 的其中一個或多個引數。</span><span class="sxs-lookup"><span data-stu-id="a177d-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="a177d-123">當做多重集 (Multiset) 建構函式的其中一個或多個引數。</span><span class="sxs-lookup"><span data-stu-id="a177d-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="a177d-124">多重集建構函式至少必須有一個引數為非 Null 常值的運算式。</span><span class="sxs-lookup"><span data-stu-id="a177d-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="a177d-125">當做 CASE 運算式中的其中一個或多個 THEN 或 ELSE 運算式。</span><span class="sxs-lookup"><span data-stu-id="a177d-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="a177d-126">CASE 運算式中至少必須有一個 THEN 或 ELSE 運算式為 Null 常值以外的運算式。</span><span class="sxs-lookup"><span data-stu-id="a177d-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="a177d-127">自由浮動 Null 常值不能在其他案例中使用。</span><span class="sxs-lookup"><span data-stu-id="a177d-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="a177d-128">例如，不能當做資料列建構函式的引數。</span><span class="sxs-lookup"><span data-stu-id="a177d-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a177d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a177d-129">See also</span></span>

- [<span data-ttu-id="a177d-130">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="a177d-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
