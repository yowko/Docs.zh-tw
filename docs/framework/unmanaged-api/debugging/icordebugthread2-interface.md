---
title: ICorDebugThread2 Interface1
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 907ba524164b1e0d167f7a88250c7d32910504f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="afe87-102">ICorDebugThread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="afe87-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="afe87-103">可做為 ICorDebugThread 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="afe87-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afe87-104">方法</span><span class="sxs-lookup"><span data-stu-id="afe87-104">Methods</span></span>  
  
|<span data-ttu-id="afe87-105">方法</span><span class="sxs-lookup"><span data-stu-id="afe87-105">Method</span></span>|<span data-ttu-id="afe87-106">描述</span><span class="sxs-lookup"><span data-stu-id="afe87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afe87-107">GetActiveFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="afe87-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="afe87-108">取得包含在執行緒框架中作用中的函式的相關資料的 COR_ACTIVE_FUNCTION 執行個體的陣列。</span><span class="sxs-lookup"><span data-stu-id="afe87-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="afe87-109">GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="afe87-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="afe87-110">取得這個連接識別碼`ICorDebugThread2`。</span><span class="sxs-lookup"><span data-stu-id="afe87-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="afe87-111">GetTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="afe87-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="afe87-112">取得這個工作識別碼`ICorDebugThread2`。</span><span class="sxs-lookup"><span data-stu-id="afe87-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="afe87-113">GetVolatileOSThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="afe87-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="afe87-114">取得這個作業系統執行緒識別項`ICorDebugThread2`。</span><span class="sxs-lookup"><span data-stu-id="afe87-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="afe87-115">InterceptCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="afe87-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="afe87-116">可讓偵錯工具攔截在執行緒上目前的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="afe87-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afe87-117">備註</span><span class="sxs-lookup"><span data-stu-id="afe87-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afe87-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="afe87-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afe87-119">需求</span><span class="sxs-lookup"><span data-stu-id="afe87-119">Requirements</span></span>  
 <span data-ttu-id="afe87-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="afe87-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe87-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afe87-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afe87-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afe87-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afe87-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afe87-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe87-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="afe87-124">See Also</span></span>  
 [<span data-ttu-id="afe87-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="afe87-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
