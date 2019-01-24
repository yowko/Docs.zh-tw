---
title: COR_PRF_FUNCTION_ARGUMENT_INFO 結構
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bb92f9ba8ff0aed1c6eb1fa44fb4d7c9abc186a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714226"
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="2a592-102">COR_PRF_FUNCTION_ARGUMENT_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="2a592-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="2a592-103">代表函式的引數，順序由左至右。</span><span class="sxs-lookup"><span data-stu-id="2a592-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a592-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a592-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2a592-105">成員</span><span class="sxs-lookup"><span data-stu-id="2a592-105">Members</span></span>  
  
|<span data-ttu-id="2a592-106">成員</span><span class="sxs-lookup"><span data-stu-id="2a592-106">Member</span></span>|<span data-ttu-id="2a592-107">描述</span><span class="sxs-lookup"><span data-stu-id="2a592-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="2a592-108">引數的區塊數目。</span><span class="sxs-lookup"><span data-stu-id="2a592-108">The number of blocks of arguments.</span></span> <span data-ttu-id="2a592-109">也就是說，這個值是數目[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構中`ranges`陣列。</span><span class="sxs-lookup"><span data-stu-id="2a592-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="2a592-110">所有引數的大小總計。</span><span class="sxs-lookup"><span data-stu-id="2a592-110">The total size of all arguments.</span></span> <span data-ttu-id="2a592-111">換句話說，這個值會是引數長度的總和。</span><span class="sxs-lookup"><span data-stu-id="2a592-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="2a592-112">陣列`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，每一個都代表一個區塊的函式引數。</span><span class="sxs-lookup"><span data-stu-id="2a592-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a592-113">備註</span><span class="sxs-lookup"><span data-stu-id="2a592-113">Remarks</span></span>  
 <span data-ttu-id="2a592-114">函式可能會有多個引數。</span><span class="sxs-lookup"><span data-stu-id="2a592-114">A function may have many arguments.</span></span> <span data-ttu-id="2a592-115">這些引數不可能在記憶體中儲存連續。</span><span class="sxs-lookup"><span data-stu-id="2a592-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="2a592-116">您可能必須在不同的位置有一個引數的最後一個區塊、 區塊的兩個引數，在另一個位置，以及在一處的三個引數的區塊。</span><span class="sxs-lookup"><span data-stu-id="2a592-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="2a592-117">這些引數都相同的函式;它們只儲存在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="2a592-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="2a592-118">`COR_PRF_FUNCTION_ARGUMENT_INFO`結構代表單一函式的所有引數。</span><span class="sxs-lookup"><span data-stu-id="2a592-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="2a592-119">它會使用陣列參考的函式引數的所有區塊。</span><span class="sxs-lookup"><span data-stu-id="2a592-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="2a592-120">因此，在單一的函式，您擁有單一`COR_PRF_FUNCTION_ARGUMENT_INFO`結構，參考多個`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，其中每一個指向一或多個函式引數。</span><span class="sxs-lookup"><span data-stu-id="2a592-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="2a592-121">會儲存在暫存器中的引數會溢出到記憶體中建立的結構。</span><span class="sxs-lookup"><span data-stu-id="2a592-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a592-122">需求</span><span class="sxs-lookup"><span data-stu-id="2a592-122">Requirements</span></span>  
 <span data-ttu-id="2a592-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a592-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a592-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="2a592-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2a592-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a592-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a592-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a592-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a592-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a592-127">See also</span></span>
- [<span data-ttu-id="2a592-128">分析結構</span><span class="sxs-lookup"><span data-stu-id="2a592-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
