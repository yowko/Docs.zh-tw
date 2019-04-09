---
title: 。 (成員存取) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 6ebedd2b381d035d199e151f64632acf7d502ff5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139707"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="8a5c4-103">。</span><span class="sxs-lookup"><span data-stu-id="8a5c4-103">.</span></span> <span data-ttu-id="8a5c4-104">(成員存取) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8a5c4-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="8a5c4-105">點運算子 （.） 是[!INCLUDE[esql](../../../../../../includes/esql-md.md)]成員存取運算子。</span><span class="sxs-lookup"><span data-stu-id="8a5c4-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="8a5c4-106">使用成員存取運算子可產生結構化概念模型型別執行個體之屬性或欄位的值。</span><span class="sxs-lookup"><span data-stu-id="8a5c4-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a5c4-107">語法</span><span class="sxs-lookup"><span data-stu-id="8a5c4-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a5c4-108">引數</span><span class="sxs-lookup"><span data-stu-id="8a5c4-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8a5c4-109">結構化概念模型型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8a5c4-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="8a5c4-110">屬於物件執行個體的屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="8a5c4-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a5c4-111">備註</span><span class="sxs-lookup"><span data-stu-id="8a5c4-111">Remarks</span></span>  
 <span data-ttu-id="8a5c4-112">點 (.) 運算子可以用來從記錄擷取欄位，就像是擷取複雜或實體類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="8a5c4-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="8a5c4-113">舉例來講，假設 Name 型別的 n 是 Person 型別的成員，且 p 是 Person 型別的執行個體，則 p.n 便是產生 Name 型別值的合法成員存取運算式。</span><span class="sxs-lookup"><span data-stu-id="8a5c4-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="8a5c4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a5c4-114">See also</span></span>

- [<span data-ttu-id="8a5c4-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="8a5c4-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
