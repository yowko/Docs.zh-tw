---
title: ICorDebugHeapSegmentEnum::Next 方法
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b63646b54b73c30abf0ddb9a06a982f1364ef87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417020"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="730ea-102">ICorDebugHeapSegmentEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="730ea-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="730ea-103">取得指定的數目[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)包含 managed 堆積的記憶體區域的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="730ea-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="730ea-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="730ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="730ea-105">Parameters</span></span>  
 <span data-ttu-id="730ea-106">celt</span><span class="sxs-lookup"><span data-stu-id="730ea-106">celt</span></span>  
 <span data-ttu-id="730ea-107">[in]要擷取的區段數目。</span><span class="sxs-lookup"><span data-stu-id="730ea-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="730ea-108">區段</span><span class="sxs-lookup"><span data-stu-id="730ea-108">segments</span></span>  
 <span data-ttu-id="730ea-109">[out]陣列的指標，其中每個指向[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)提供 managed 堆積中記憶體區域資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="730ea-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="730ea-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="730ea-110">pceltFetched</span></span>  
 <span data-ttu-id="730ea-111">[out]數目的指標[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)中實際傳回的物件`segments`。</span><span class="sxs-lookup"><span data-stu-id="730ea-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="730ea-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="730ea-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="730ea-113">備註</span><span class="sxs-lookup"><span data-stu-id="730ea-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730ea-114">需求</span><span class="sxs-lookup"><span data-stu-id="730ea-114">Requirements</span></span>  
 <span data-ttu-id="730ea-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="730ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="730ea-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="730ea-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="730ea-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="730ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="730ea-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="730ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730ea-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="730ea-119">See Also</span></span>  
 [<span data-ttu-id="730ea-120">ICorDebugHeapSegmentEnum 介面</span><span class="sxs-lookup"><span data-stu-id="730ea-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="730ea-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="730ea-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
