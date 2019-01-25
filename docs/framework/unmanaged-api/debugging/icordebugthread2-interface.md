---
title: ICorDebugThread2 介面 1
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3826bfd16d3cf7534a6e920c516987908547b419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716140"
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="0acc1-102">ICorDebugThread2 介面 1</span><span class="sxs-lookup"><span data-stu-id="0acc1-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="0acc1-103">可做為 ICorDebugThread 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="0acc1-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0acc1-104">方法</span><span class="sxs-lookup"><span data-stu-id="0acc1-104">Methods</span></span>  
  
|<span data-ttu-id="0acc1-105">方法</span><span class="sxs-lookup"><span data-stu-id="0acc1-105">Method</span></span>|<span data-ttu-id="0acc1-106">描述</span><span class="sxs-lookup"><span data-stu-id="0acc1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0acc1-107">GetActiveFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="0acc1-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="0acc1-108">取得包含執行緒的框架中作用中的函式的相關資料的 COR_ACTIVE_FUNCTION 執行個體的陣列。</span><span class="sxs-lookup"><span data-stu-id="0acc1-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="0acc1-109">GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="0acc1-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="0acc1-110">取得這個連接識別碼`ICorDebugThread2`。</span><span class="sxs-lookup"><span data-stu-id="0acc1-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="0acc1-111">GetTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="0acc1-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="0acc1-112">取得這個工作識別碼`ICorDebugThread2`。</span><span class="sxs-lookup"><span data-stu-id="0acc1-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="0acc1-113">GetVolatileOSThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="0acc1-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="0acc1-114">取得這個作業系統執行緒識別項`ICorDebugThread2`。</span><span class="sxs-lookup"><span data-stu-id="0acc1-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="0acc1-115">InterceptCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="0acc1-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="0acc1-116">可讓偵錯工具攔截在執行緒上目前的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0acc1-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0acc1-117">備註</span><span class="sxs-lookup"><span data-stu-id="0acc1-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acc1-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0acc1-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0acc1-119">需求</span><span class="sxs-lookup"><span data-stu-id="0acc1-119">Requirements</span></span>  
 <span data-ttu-id="0acc1-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0acc1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0acc1-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0acc1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0acc1-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0acc1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0acc1-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0acc1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acc1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0acc1-124">See also</span></span>
- [<span data-ttu-id="0acc1-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0acc1-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
