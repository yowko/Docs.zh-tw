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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d703b2467d508324f3eb39b822c239484ac1c6e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="5a889-102">位元標準函式</span><span class="sxs-lookup"><span data-stu-id="5a889-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5a889-103"> 包含位元標準函式。</span><span class="sxs-lookup"><span data-stu-id="5a889-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a889-104">備註</span><span class="sxs-lookup"><span data-stu-id="5a889-104">Remarks</span></span>  
 <span data-ttu-id="5a889-105">下表將顯示位元 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。</span><span class="sxs-lookup"><span data-stu-id="5a889-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="5a889-106">這些函式會傳回`Null`如果`Null`輸入提供。</span><span class="sxs-lookup"><span data-stu-id="5a889-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="5a889-107">這些函式的傳回型別與引數型別相同。</span><span class="sxs-lookup"><span data-stu-id="5a889-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="5a889-108">引數必須屬於相同的型別 (如果函式接受多個引數的話)。</span><span class="sxs-lookup"><span data-stu-id="5a889-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="5a889-109">若要針對不同的型別執行位元運算，您必須明確轉型為相同的型別。</span><span class="sxs-lookup"><span data-stu-id="5a889-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="5a889-110">功能</span><span class="sxs-lookup"><span data-stu-id="5a889-110">Function</span></span>|<span data-ttu-id="5a889-111">描述</span><span class="sxs-lookup"><span data-stu-id="5a889-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5a889-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="5a889-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="5a889-113">傳回 `value1` 和 `value2` 的位元結合，作為 `value1` 和 `value2` 的型別。</span><span class="sxs-lookup"><span data-stu-id="5a889-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="5a889-114">**引數**</span><span class="sxs-lookup"><span data-stu-id="5a889-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="5a889-115">A `Byte`， `Int16`， `Int32`，和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="5a889-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="5a889-116">**範例**</span><span class="sxs-lookup"><span data-stu-id="5a889-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="5a889-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="5a889-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="5a889-118">傳回 `value` 的位元否定。</span><span class="sxs-lookup"><span data-stu-id="5a889-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="5a889-119">**引數**</span><span class="sxs-lookup"><span data-stu-id="5a889-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="5a889-120">A `Byte`， `Int16`， `Int32`，和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="5a889-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="5a889-121">**範例**</span><span class="sxs-lookup"><span data-stu-id="5a889-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="5a889-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="5a889-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="5a889-123">傳回 `value1` 和 `value2` 的位元分離，作為 `value1` 和 `value2` 的型別。</span><span class="sxs-lookup"><span data-stu-id="5a889-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="5a889-124">**引數**</span><span class="sxs-lookup"><span data-stu-id="5a889-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="5a889-125">A `Byte`， `Int16`，`Int32`和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="5a889-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="5a889-126">**範例**</span><span class="sxs-lookup"><span data-stu-id="5a889-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="5a889-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="5a889-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="5a889-128">傳回 `value1` 和 `value2` 的位元排除分離，作為 `value1` 和 `value2` 的型別。</span><span class="sxs-lookup"><span data-stu-id="5a889-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="5a889-129">**引數**</span><span class="sxs-lookup"><span data-stu-id="5a889-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="5a889-130">A `Byte`， `Int16`，`Int32`和`Int64`。</span><span class="sxs-lookup"><span data-stu-id="5a889-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="5a889-131">**範例**</span><span class="sxs-lookup"><span data-stu-id="5a889-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="5a889-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a889-132">See Also</span></span>  
 [<span data-ttu-id="5a889-133">標準函式</span><span class="sxs-lookup"><span data-stu-id="5a889-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
