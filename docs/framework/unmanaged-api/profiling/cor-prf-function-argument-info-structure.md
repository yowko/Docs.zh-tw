---
title: "COR_PRF_FUNCTION_ARGUMENT_INFO 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e26377fe3c5cfbae68f90087e3fb624ae4db0dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="29a02-102">COR_PRF_FUNCTION_ARGUMENT_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="29a02-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="29a02-103">代表函式的引數，順序由左至右。</span><span class="sxs-lookup"><span data-stu-id="29a02-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a02-104">語法</span><span class="sxs-lookup"><span data-stu-id="29a02-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="29a02-105">成員</span><span class="sxs-lookup"><span data-stu-id="29a02-105">Members</span></span>  
  
|<span data-ttu-id="29a02-106">成員</span><span class="sxs-lookup"><span data-stu-id="29a02-106">Member</span></span>|<span data-ttu-id="29a02-107">描述</span><span class="sxs-lookup"><span data-stu-id="29a02-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="29a02-108">引數的區塊數目。</span><span class="sxs-lookup"><span data-stu-id="29a02-108">The number of blocks of arguments.</span></span> <span data-ttu-id="29a02-109">也就是說，這個值是數目[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)中結構`ranges`陣列。</span><span class="sxs-lookup"><span data-stu-id="29a02-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="29a02-110">所有引數的大小總計。</span><span class="sxs-lookup"><span data-stu-id="29a02-110">The total size of all arguments.</span></span> <span data-ttu-id="29a02-111">換句話說，這個值會是引數長度的總和。</span><span class="sxs-lookup"><span data-stu-id="29a02-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="29a02-112">陣列`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，其中每一個都代表一個區塊函式引數。</span><span class="sxs-lookup"><span data-stu-id="29a02-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29a02-113">備註</span><span class="sxs-lookup"><span data-stu-id="29a02-113">Remarks</span></span>  
 <span data-ttu-id="29a02-114">函式可能會有多個引數。</span><span class="sxs-lookup"><span data-stu-id="29a02-114">A function may have many arguments.</span></span> <span data-ttu-id="29a02-115">這些引數可能會不會由左至右連續儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="29a02-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="29a02-116">您可能必須區塊的兩個引數中的其他位置，以及最後一個區塊中的不同位置有一個引數的一個位置中的三個引數區塊。</span><span class="sxs-lookup"><span data-stu-id="29a02-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="29a02-117">這些引數都相同的函式。它們只儲存在不同的地方。</span><span class="sxs-lookup"><span data-stu-id="29a02-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="29a02-118">`COR_PRF_FUNCTION_ARGUMENT_INFO`結構表示的單一函式的所有引數。</span><span class="sxs-lookup"><span data-stu-id="29a02-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="29a02-119">它會使用陣列參考的函式引數的所有區塊。</span><span class="sxs-lookup"><span data-stu-id="29a02-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="29a02-120">因此，在單一函式，您有單一`COR_PRF_FUNCTION_ARGUMENT_INFO`結構，它會參考多個`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，其中每個指向一個或多個函式引數。</span><span class="sxs-lookup"><span data-stu-id="29a02-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="29a02-121">儲存在暫存器中的引數會溢出到記憶體，建立結構。</span><span class="sxs-lookup"><span data-stu-id="29a02-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29a02-122">需求</span><span class="sxs-lookup"><span data-stu-id="29a02-122">Requirements</span></span>  
 <span data-ttu-id="29a02-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29a02-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29a02-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="29a02-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="29a02-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29a02-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29a02-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29a02-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a02-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="29a02-127">See Also</span></span>  
 [<span data-ttu-id="29a02-128">分析結構</span><span class="sxs-lookup"><span data-stu-id="29a02-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
