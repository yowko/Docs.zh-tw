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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6419a525a8a542295751defb97e67a83220730b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965071"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="7faf2-102">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="7faf2-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="7faf2-103">代表目前執行程式碼的電腦上可用的暫存器集合。</span><span class="sxs-lookup"><span data-stu-id="7faf2-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7faf2-104">方法</span><span class="sxs-lookup"><span data-stu-id="7faf2-104">Methods</span></span>  
  
|<span data-ttu-id="7faf2-105">方法</span><span class="sxs-lookup"><span data-stu-id="7faf2-105">Method</span></span>|<span data-ttu-id="7faf2-106">描述</span><span class="sxs-lookup"><span data-stu-id="7faf2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7faf2-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="7faf2-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="7faf2-108">取得位元遮罩所指定之每個暫存器 (目前執行程式碼的電腦) 的值。</span><span class="sxs-lookup"><span data-stu-id="7faf2-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="7faf2-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="7faf2-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="7faf2-110">取得位元遮罩, 指出目前有哪些`ICorDebugRegisterSet`暫存器可供使用。</span><span class="sxs-lookup"><span data-stu-id="7faf2-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="7faf2-111">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="7faf2-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="7faf2-112">取得目前線程的內容。</span><span class="sxs-lookup"><span data-stu-id="7faf2-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="7faf2-113">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="7faf2-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="7faf2-114">未針對 .NET Framework 版本2.0 進行執行。</span><span class="sxs-lookup"><span data-stu-id="7faf2-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="7faf2-115">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="7faf2-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="7faf2-116">未針對 .NET Framework 2.0 執行。</span><span class="sxs-lookup"><span data-stu-id="7faf2-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7faf2-117">備註</span><span class="sxs-lookup"><span data-stu-id="7faf2-117">Remarks</span></span>  
 <span data-ttu-id="7faf2-118">`ICorDebugRegisterSet`介面僅支援32位暫存器。</span><span class="sxs-lookup"><span data-stu-id="7faf2-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="7faf2-119">在需要額外暫存器的平臺 (例如 IA-64) 上使用[ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7faf2-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7faf2-120">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7faf2-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7faf2-121">需求</span><span class="sxs-lookup"><span data-stu-id="7faf2-121">Requirements</span></span>  
 <span data-ttu-id="7faf2-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7faf2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7faf2-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7faf2-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7faf2-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7faf2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7faf2-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7faf2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7faf2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7faf2-126">See also</span></span>

- [<span data-ttu-id="7faf2-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7faf2-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7faf2-128">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="7faf2-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
