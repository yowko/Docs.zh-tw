---
title: ICorDebugFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936997"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="197e7-102">ICorDebugFrame 介面</span><span class="sxs-lookup"><span data-stu-id="197e7-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="197e7-103">表示目前堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="197e7-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="197e7-104">方法</span><span class="sxs-lookup"><span data-stu-id="197e7-104">Methods</span></span>  
  
|<span data-ttu-id="197e7-105">方法</span><span class="sxs-lookup"><span data-stu-id="197e7-105">Method</span></span>|<span data-ttu-id="197e7-106">描述</span><span class="sxs-lookup"><span data-stu-id="197e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="197e7-107">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="197e7-108">取得 ICorDebugStepper, 以執行相對於這個`ICorDebugFrame`的逐步操作。</span><span class="sxs-lookup"><span data-stu-id="197e7-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="197e7-109">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="197e7-110">取得此框架所呼叫`ICorDebugFrame`之目前鏈中的指標, 如果這是鏈中最內層的框架, 則會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="197e7-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="197e7-111">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="197e7-112">取得目前鏈中呼叫`ICorDebugFrame`此框架的指標, 如果這是鏈中最外層的框架, 則會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="197e7-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="197e7-113">GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="197e7-114">取得此`ICorDebugFrame`所屬 ICorDebugChain 的指標。</span><span class="sxs-lookup"><span data-stu-id="197e7-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="197e7-115">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="197e7-116">取得與這個堆疊框架相關聯之 ICorDebugCode 的指標。</span><span class="sxs-lookup"><span data-stu-id="197e7-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="197e7-117">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="197e7-118">取得 ICorDebugFunction 的指標, 其中包含與這個堆疊框架相關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="197e7-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="197e7-119">GetFunctionToken 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="197e7-120">取得包含與此堆疊框架相關聯之程式碼的函式的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="197e7-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="197e7-121">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="197e7-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="197e7-122">取得這個`ICorDebugFrame`所表示之堆疊框架的絕對位址範圍。</span><span class="sxs-lookup"><span data-stu-id="197e7-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="197e7-123">備註</span><span class="sxs-lookup"><span data-stu-id="197e7-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="197e7-124">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="197e7-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="197e7-125">需求</span><span class="sxs-lookup"><span data-stu-id="197e7-125">Requirements</span></span>  
 <span data-ttu-id="197e7-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="197e7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="197e7-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="197e7-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="197e7-128">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="197e7-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="197e7-129">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="197e7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197e7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="197e7-130">See also</span></span>

- [<span data-ttu-id="197e7-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="197e7-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
