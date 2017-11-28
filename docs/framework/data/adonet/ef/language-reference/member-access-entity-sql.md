---
title: ". (成員存取) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c9d5d8f2c90273b316379d3c2803835bab3faef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="7d6f2-103">。</span><span class="sxs-lookup"><span data-stu-id="7d6f2-103">.</span></span> <span data-ttu-id="7d6f2-104">(成員存取) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7d6f2-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="7d6f2-105">點運算子 （.） 是[!INCLUDE[esql](../../../../../../includes/esql-md.md)]成員存取運算子。</span><span class="sxs-lookup"><span data-stu-id="7d6f2-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="7d6f2-106">使用成員存取運算子可產生結構化概念模型型別執行個體之屬性或欄位的值。</span><span class="sxs-lookup"><span data-stu-id="7d6f2-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6f2-107">語法</span><span class="sxs-lookup"><span data-stu-id="7d6f2-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d6f2-108">引數</span><span class="sxs-lookup"><span data-stu-id="7d6f2-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7d6f2-109">結構化概念模型型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d6f2-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="7d6f2-110">屬於物件執行個體的屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="7d6f2-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d6f2-111">備註</span><span class="sxs-lookup"><span data-stu-id="7d6f2-111">Remarks</span></span>  
 <span data-ttu-id="7d6f2-112">點 (.) 運算子可以用來從記錄擷取欄位，就像是擷取複雜或實體類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="7d6f2-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="7d6f2-113">舉例來講，假設 Name 型別的 n 是 Person 型別的成員，且 p 是 Person 型別的執行個體，則 p.n 便是產生 Name 型別值的合法成員存取運算式。</span><span class="sxs-lookup"><span data-stu-id="7d6f2-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="7d6f2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d6f2-114">See Also</span></span>  
 [<span data-ttu-id="7d6f2-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="7d6f2-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
