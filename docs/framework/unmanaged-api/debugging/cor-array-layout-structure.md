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
ms.openlocfilehash: 2ca6c89a671c4d7882e7cefdb820d07ac5636530
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727402"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="22739-102">COR_ARRAY_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="22739-102">COR_ARRAY_LAYOUT Structure</span></span>

<span data-ttu-id="22739-103">提供記憶體中陣列物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="22739-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22739-104">語法</span><span class="sxs-lookup"><span data-stu-id="22739-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="22739-105">成員</span><span class="sxs-lookup"><span data-stu-id="22739-105">Members</span></span>  
  
|<span data-ttu-id="22739-106">member</span><span class="sxs-lookup"><span data-stu-id="22739-106">Member</span></span>|<span data-ttu-id="22739-107">描述</span><span class="sxs-lookup"><span data-stu-id="22739-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="22739-108">陣列所包含物件類型的識別碼。</span><span class="sxs-lookup"><span data-stu-id="22739-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="22739-109">CorElementType 列舉值，指出元件是否為垃圾收集參考、實值類別或基本。</span><span class="sxs-lookup"><span data-stu-id="22739-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="22739-110">陣列中第一個元素的位移。</span><span class="sxs-lookup"><span data-stu-id="22739-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="22739-111">每個元素的大小。</span><span class="sxs-lookup"><span data-stu-id="22739-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="22739-112">陣列中元素數目的位移。</span><span class="sxs-lookup"><span data-stu-id="22739-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="22739-113">順位的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="22739-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="22739-114">陣列中的排名數目。</span><span class="sxs-lookup"><span data-stu-id="22739-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="22739-115">排名開始的位移。</span><span class="sxs-lookup"><span data-stu-id="22739-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22739-116">備註</span><span class="sxs-lookup"><span data-stu-id="22739-116">Remarks</span></span>  

 <span data-ttu-id="22739-117">`rankSize`欄位會指定多維度陣列中的順位大小。</span><span class="sxs-lookup"><span data-stu-id="22739-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="22739-118">這對一維陣列而言也是正確的。</span><span class="sxs-lookup"><span data-stu-id="22739-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="22739-119">`numRanks`針對一維陣列和 `N` 維度的多維陣列，的值為 1 `N` 。</span><span class="sxs-lookup"><span data-stu-id="22739-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22739-120">需求</span><span class="sxs-lookup"><span data-stu-id="22739-120">Requirements</span></span>  

 <span data-ttu-id="22739-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22739-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22739-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22739-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22739-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22739-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22739-124">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22739-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22739-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22739-125">See also</span></span>

- [<span data-ttu-id="22739-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="22739-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="22739-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="22739-127">Debugging</span></span>](index.md)
