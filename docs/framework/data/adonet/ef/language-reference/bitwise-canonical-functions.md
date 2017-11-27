---
title: "位元標準函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a20f9675af5a67291d95a9297b1ffa1c81a80522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="f3a1e-102">位元標準函式</span><span class="sxs-lookup"><span data-stu-id="f3a1e-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f3a1e-103"> 包含位元標準函式。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3a1e-104">備註</span><span class="sxs-lookup"><span data-stu-id="f3a1e-104">Remarks</span></span>  
 <span data-ttu-id="f3a1e-105">下表將顯示位元 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="f3a1e-106">這些函式會傳回`Null`如果`Null`輸入提供。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="f3a1e-107">這些函式的傳回型別與引數型別相同。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="f3a1e-108">引數必須屬於相同的型別 (如果函式接受多個引數的話)。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="f3a1e-109">若要針對不同的型別執行位元運算，您必須明確轉型為相同的型別。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="f3a1e-110">函式</span><span class="sxs-lookup"><span data-stu-id="f3a1e-110">Function</span></span>|<span data-ttu-id="f3a1e-111">說明</span><span class="sxs-lookup"><span data-stu-id="f3a1e-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f3a1e-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="f3a1e-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="f3a1e-113">傳回 `value1` 和 `value2` 的位元結合，作為 `value1` 和 `value2` 的型別。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="f3a1e-114">**引數**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="f3a1e-115">A `Byte`， `Int16`， `Int32`，和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="f3a1e-116">**範例**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="f3a1e-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="f3a1e-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="f3a1e-118">傳回 `value` 的位元否定。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="f3a1e-119">**引數**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="f3a1e-120">A `Byte`， `Int16`， `Int32`，和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="f3a1e-121">**範例**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="f3a1e-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="f3a1e-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="f3a1e-123">傳回 `value1` 和 `value2` 的位元分離，作為 `value1` 和 `value2` 的型別。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="f3a1e-124">**引數**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="f3a1e-125">A `Byte`， `Int16`，`Int32`和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="f3a1e-126">**範例**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="f3a1e-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="f3a1e-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="f3a1e-128">傳回 `value1` 和 `value2` 的位元排除分離，作為 `value1` 和 `value2` 的型別。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="f3a1e-129">**引數**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="f3a1e-130">A `Byte`， `Int16`，`Int32`和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="f3a1e-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="f3a1e-131">**範例**</span><span class="sxs-lookup"><span data-stu-id="f3a1e-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="f3a1e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3a1e-132">See Also</span></span>  
 [<span data-ttu-id="f3a1e-133">標準函式</span><span class="sxs-lookup"><span data-stu-id="f3a1e-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
