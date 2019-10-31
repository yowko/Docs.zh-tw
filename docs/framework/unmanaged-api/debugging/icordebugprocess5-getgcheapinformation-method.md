---
title: ICorDebugProcess5::GetGCHeapInformation 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 3aa9fe884b16a239f5105dd262edeb8fc3e4abaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084411"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="67965-102">ICorDebugProcess5::GetGCHeapInformation 方法</span><span class="sxs-lookup"><span data-stu-id="67965-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="67965-103">提供有關垃圾收集堆積的一般資訊，包括目前是否可列舉。</span><span class="sxs-lookup"><span data-stu-id="67965-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67965-104">語法</span><span class="sxs-lookup"><span data-stu-id="67965-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67965-105">參數</span><span class="sxs-lookup"><span data-stu-id="67965-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="67965-106">脫銷[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)值的指標，提供有關垃圾收集堆積的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="67965-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67965-107">備註</span><span class="sxs-lookup"><span data-stu-id="67965-107">Remarks</span></span>  
 <span data-ttu-id="67965-108">在列舉堆積或個別堆積區域之前，必須先呼叫 `ICorDebugProcess5::GetGCHeapInformation` 方法，以確保進程中的垃圾收集結構目前有效。</span><span class="sxs-lookup"><span data-stu-id="67965-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="67965-109">當集合正在進行時，無法逐步執行垃圾收集堆積。</span><span class="sxs-lookup"><span data-stu-id="67965-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="67965-110">否則，列舉可能會捕捉到不正確垃圾收集結構。</span><span class="sxs-lookup"><span data-stu-id="67965-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67965-111">需求</span><span class="sxs-lookup"><span data-stu-id="67965-111">Requirements</span></span>  
 <span data-ttu-id="67965-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67965-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67965-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67965-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67965-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67965-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67965-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67965-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67965-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="67965-116">See also</span></span>

- [<span data-ttu-id="67965-117">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="67965-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="67965-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="67965-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
