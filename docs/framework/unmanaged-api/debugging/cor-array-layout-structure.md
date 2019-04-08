---
title: COR_ARRAY_LAYOUT 結構
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a5a5bb26912c87cdf37ba0d8f0cee1cf1ffa97
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142008"
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="23ac0-102">COR_ARRAY_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="23ac0-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="23ac0-103">提供記憶體中陣列物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="23ac0-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ac0-104">語法</span><span class="sxs-lookup"><span data-stu-id="23ac0-104">Syntax</span></span>  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="23ac0-105">成員</span><span class="sxs-lookup"><span data-stu-id="23ac0-105">Members</span></span>  
  
|<span data-ttu-id="23ac0-106">成員</span><span class="sxs-lookup"><span data-stu-id="23ac0-106">Member</span></span>|<span data-ttu-id="23ac0-107">描述</span><span class="sxs-lookup"><span data-stu-id="23ac0-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="23ac0-108">陣列包含的物件類型的識別項。</span><span class="sxs-lookup"><span data-stu-id="23ac0-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="23ac0-109">CorElementType 列舉值，指出元件是否記憶體回收參考、 實值類別或基本型別。</span><span class="sxs-lookup"><span data-stu-id="23ac0-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="23ac0-110">要在陣列中的第一個元素的位移。</span><span class="sxs-lookup"><span data-stu-id="23ac0-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="23ac0-111">每個項目的大小。</span><span class="sxs-lookup"><span data-stu-id="23ac0-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="23ac0-112">要在陣列中的項目數的位移。</span><span class="sxs-lookup"><span data-stu-id="23ac0-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="23ac0-113">陣序規範，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="23ac0-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="23ac0-114">陣列中的排列次序的數目。</span><span class="sxs-lookup"><span data-stu-id="23ac0-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="23ac0-115">陣序規範的開始位移。</span><span class="sxs-lookup"><span data-stu-id="23ac0-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23ac0-116">備註</span><span class="sxs-lookup"><span data-stu-id="23ac0-116">Remarks</span></span>  
 <span data-ttu-id="23ac0-117">`rankSize`欄位多維陣列中指定的陣序規範的大小。</span><span class="sxs-lookup"><span data-stu-id="23ac0-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="23ac0-118">它是精確的單一維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="23ac0-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="23ac0-119">值`numRanks`為 1 的一維陣列並`N`多維陣列的`N`維度。</span><span class="sxs-lookup"><span data-stu-id="23ac0-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23ac0-120">需求</span><span class="sxs-lookup"><span data-stu-id="23ac0-120">Requirements</span></span>  
 <span data-ttu-id="23ac0-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23ac0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ac0-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23ac0-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23ac0-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23ac0-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="23ac0-124">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="23ac0-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23ac0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23ac0-125">See also</span></span>

- [<span data-ttu-id="23ac0-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="23ac0-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="23ac0-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="23ac0-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
