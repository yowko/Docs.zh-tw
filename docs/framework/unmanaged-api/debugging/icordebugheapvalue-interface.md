---
title: ICorDebugHeapValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5fcd8c17c4006714fa9d11aece5cccc57c97087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700822"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="0935d-102">ICorDebugHeapValue 介面</span><span class="sxs-lookup"><span data-stu-id="0935d-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="0935d-103">「 ICorDebugValue"，表示已由 common language runtime (CLR) 記憶體回收行程回收物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="0935d-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0935d-104">方法</span><span class="sxs-lookup"><span data-stu-id="0935d-104">Methods</span></span>  
  
|<span data-ttu-id="0935d-105">方法</span><span class="sxs-lookup"><span data-stu-id="0935d-105">Method</span></span>|<span data-ttu-id="0935d-106">描述</span><span class="sxs-lookup"><span data-stu-id="0935d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0935d-107">CreateRelocBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="0935d-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="0935d-108">未實作。</span><span class="sxs-lookup"><span data-stu-id="0935d-108">Not implemented.</span></span>|  
|[<span data-ttu-id="0935d-109">IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="0935d-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="0935d-110">取得值，表示物件是否表示由此`ICorDebugHeapValue`有效，或已經由記憶體回收行程回收。</span><span class="sxs-lookup"><span data-stu-id="0935d-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="0935d-111">這個方法已被取代，在.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="0935d-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0935d-112">備註</span><span class="sxs-lookup"><span data-stu-id="0935d-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0935d-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0935d-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0935d-114">需求</span><span class="sxs-lookup"><span data-stu-id="0935d-114">Requirements</span></span>  
 <span data-ttu-id="0935d-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0935d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0935d-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0935d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0935d-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0935d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0935d-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0935d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0935d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0935d-119">See also</span></span>

- [<span data-ttu-id="0935d-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0935d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
