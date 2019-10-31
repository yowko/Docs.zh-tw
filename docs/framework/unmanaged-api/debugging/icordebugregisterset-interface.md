---
title: ICorDebugRegisterSet 介面
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 1ea0274adc12f3a99df0422bfc0b5180f0ef5596
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131383"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="c23d2-102">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="c23d2-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="c23d2-103">代表目前執行程式碼的電腦上可用的暫存器集合。</span><span class="sxs-lookup"><span data-stu-id="c23d2-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c23d2-104">方法</span><span class="sxs-lookup"><span data-stu-id="c23d2-104">Methods</span></span>  
  
|<span data-ttu-id="c23d2-105">方法</span><span class="sxs-lookup"><span data-stu-id="c23d2-105">Method</span></span>|<span data-ttu-id="c23d2-106">描述</span><span class="sxs-lookup"><span data-stu-id="c23d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c23d2-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="c23d2-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="c23d2-108">取得位元遮罩所指定之每個暫存器（目前執行程式碼的電腦）的值。</span><span class="sxs-lookup"><span data-stu-id="c23d2-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="c23d2-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="c23d2-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="c23d2-110">取得位元遮罩，指出此 `ICorDebugRegisterSet` 中的哪些暫存器目前可供使用。</span><span class="sxs-lookup"><span data-stu-id="c23d2-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="c23d2-111">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="c23d2-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="c23d2-112">取得目前線程的內容。</span><span class="sxs-lookup"><span data-stu-id="c23d2-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="c23d2-113">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="c23d2-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="c23d2-114">未針對 .NET Framework 版本2.0 進行執行。</span><span class="sxs-lookup"><span data-stu-id="c23d2-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="c23d2-115">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="c23d2-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="c23d2-116">未針對 .NET Framework 2.0 執行。</span><span class="sxs-lookup"><span data-stu-id="c23d2-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c23d2-117">備註</span><span class="sxs-lookup"><span data-stu-id="c23d2-117">Remarks</span></span>  
 <span data-ttu-id="c23d2-118">`ICorDebugRegisterSet` 介面僅支援32位暫存器。</span><span class="sxs-lookup"><span data-stu-id="c23d2-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="c23d2-119">在需要額外暫存器的平臺（例如 IA-64）上使用[ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="c23d2-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c23d2-120">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c23d2-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c23d2-121">需求</span><span class="sxs-lookup"><span data-stu-id="c23d2-121">Requirements</span></span>  
 <span data-ttu-id="c23d2-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c23d2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c23d2-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c23d2-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c23d2-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c23d2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c23d2-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c23d2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23d2-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="c23d2-126">See also</span></span>

- [<span data-ttu-id="c23d2-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c23d2-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c23d2-128">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="c23d2-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
