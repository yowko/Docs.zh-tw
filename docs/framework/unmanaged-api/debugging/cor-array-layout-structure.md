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
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179345"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="43d15-102">COR_ARRAY_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="43d15-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="43d15-103">提供記憶體中陣列物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="43d15-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d15-104">語法</span><span class="sxs-lookup"><span data-stu-id="43d15-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="43d15-105">成員</span><span class="sxs-lookup"><span data-stu-id="43d15-105">Members</span></span>  
  
|<span data-ttu-id="43d15-106">member</span><span class="sxs-lookup"><span data-stu-id="43d15-106">Member</span></span>|<span data-ttu-id="43d15-107">描述</span><span class="sxs-lookup"><span data-stu-id="43d15-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="43d15-108">陣列包含的物件類型的識別碼。</span><span class="sxs-lookup"><span data-stu-id="43d15-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="43d15-109">CorElementType 枚舉值，用於指示元件是垃圾回收引用、值類還是基元。</span><span class="sxs-lookup"><span data-stu-id="43d15-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="43d15-110">陣列中第一個元素的偏移量。</span><span class="sxs-lookup"><span data-stu-id="43d15-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="43d15-111">每個元素的大小。</span><span class="sxs-lookup"><span data-stu-id="43d15-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="43d15-112">陣列中元素數的偏移量。</span><span class="sxs-lookup"><span data-stu-id="43d15-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="43d15-113">排名的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="43d15-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="43d15-114">陣列中的排名數。</span><span class="sxs-lookup"><span data-stu-id="43d15-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="43d15-115">排名開始的偏移量。</span><span class="sxs-lookup"><span data-stu-id="43d15-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43d15-116">備註</span><span class="sxs-lookup"><span data-stu-id="43d15-116">Remarks</span></span>  
 <span data-ttu-id="43d15-117">該`rankSize`欄位指定多維陣列中排名的大小。</span><span class="sxs-lookup"><span data-stu-id="43d15-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="43d15-118">對於單維陣列來說，它也是準確的。</span><span class="sxs-lookup"><span data-stu-id="43d15-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="43d15-119">對於單維`numRanks`陣列和`N`多維`N`維度陣列，值為 1。</span><span class="sxs-lookup"><span data-stu-id="43d15-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43d15-120">需求</span><span class="sxs-lookup"><span data-stu-id="43d15-120">Requirements</span></span>  
 <span data-ttu-id="43d15-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43d15-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43d15-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43d15-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43d15-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43d15-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43d15-124">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43d15-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43d15-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43d15-125">See also</span></span>

- [<span data-ttu-id="43d15-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="43d15-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="43d15-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="43d15-127">Debugging</span></span>](index.md)
