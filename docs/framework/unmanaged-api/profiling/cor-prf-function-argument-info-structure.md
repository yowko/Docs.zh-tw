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
ms.openlocfilehash: 2b01acbd617b13a64ef3dca6c8661f1e6bb067ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447378"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="d2a16-102">COR_PRF_FUNCTION_ARGUMENT_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="d2a16-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="d2a16-103">代表函式的引數，順序由左至右。</span><span class="sxs-lookup"><span data-stu-id="d2a16-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a16-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2a16-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d2a16-105">Members</span><span class="sxs-lookup"><span data-stu-id="d2a16-105">Members</span></span>  
  
|<span data-ttu-id="d2a16-106">成員</span><span class="sxs-lookup"><span data-stu-id="d2a16-106">Member</span></span>|<span data-ttu-id="d2a16-107">描述</span><span class="sxs-lookup"><span data-stu-id="d2a16-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="d2a16-108">引數的區塊數目。</span><span class="sxs-lookup"><span data-stu-id="d2a16-108">The number of blocks of arguments.</span></span> <span data-ttu-id="d2a16-109">也就是說，此值是 `ranges` 陣列中[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構的數目。</span><span class="sxs-lookup"><span data-stu-id="d2a16-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="d2a16-110">所有引數的總大小。</span><span class="sxs-lookup"><span data-stu-id="d2a16-110">The total size of all arguments.</span></span> <span data-ttu-id="d2a16-111">換句話說，此值是引數長度的總和。</span><span class="sxs-lookup"><span data-stu-id="d2a16-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="d2a16-112">`COR_PRF_FUNCTION_ARGUMENT_RANGE` 結構的陣列，其中每一個都代表一個函式引數的區塊。</span><span class="sxs-lookup"><span data-stu-id="d2a16-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2a16-113">備註</span><span class="sxs-lookup"><span data-stu-id="d2a16-113">Remarks</span></span>  
 <span data-ttu-id="d2a16-114">函數可能有許多引數。</span><span class="sxs-lookup"><span data-stu-id="d2a16-114">A function may have many arguments.</span></span> <span data-ttu-id="d2a16-115">這些引數可能不會連續儲存于記憶體中。</span><span class="sxs-lookup"><span data-stu-id="d2a16-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="d2a16-116">在一個位置中，您可能會有三個引數的區塊、另一個位置的兩個引數區塊，以及在不同位置的一個引數的最後一個區塊。</span><span class="sxs-lookup"><span data-stu-id="d2a16-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="d2a16-117">這些引數全都適用于相同的函式;它們只會儲存在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="d2a16-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="d2a16-118">`COR_PRF_FUNCTION_ARGUMENT_INFO` 結構代表單一函式的所有引數。</span><span class="sxs-lookup"><span data-stu-id="d2a16-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="d2a16-119">它會使用陣列來參考函數引數的所有區塊。</span><span class="sxs-lookup"><span data-stu-id="d2a16-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="d2a16-120">因此，在單一函式中，您會有一個參考多個 `COR_PRF_FUNCTION_ARGUMENT_RANGE` 結構的單一 `COR_PRF_FUNCTION_ARGUMENT_INFO` 結構，每一個都指向一個或多個函式引數。</span><span class="sxs-lookup"><span data-stu-id="d2a16-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="d2a16-121">儲存在暫存器中的引數會溢出到記憶體中，以建立結構。</span><span class="sxs-lookup"><span data-stu-id="d2a16-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a16-122">需求</span><span class="sxs-lookup"><span data-stu-id="d2a16-122">Requirements</span></span>  
 <span data-ttu-id="d2a16-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a16-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a16-124">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="d2a16-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d2a16-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2a16-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2a16-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a16-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a16-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2a16-127">See also</span></span>

- [<span data-ttu-id="d2a16-128">分析結構</span><span class="sxs-lookup"><span data-stu-id="d2a16-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
