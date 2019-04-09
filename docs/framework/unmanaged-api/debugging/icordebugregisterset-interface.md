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
ms.openlocfilehash: 7b0a5d80d984a3c696b178c4d8c936bd47354945
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135235"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="1c747-102">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="1c747-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="1c747-103">代表目前正在執行的程式碼的電腦上的可用暫存器組。</span><span class="sxs-lookup"><span data-stu-id="1c747-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c747-104">方法</span><span class="sxs-lookup"><span data-stu-id="1c747-104">Methods</span></span>  
  
|<span data-ttu-id="1c747-105">方法</span><span class="sxs-lookup"><span data-stu-id="1c747-105">Method</span></span>|<span data-ttu-id="1c747-106">描述</span><span class="sxs-lookup"><span data-stu-id="1c747-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c747-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="1c747-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="1c747-108">取得每個暫存器值 （在電腦上目前正在執行的程式碼） 所指定的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="1c747-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="1c747-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="1c747-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="1c747-110">取得位元遮罩，指出其會登錄在此`ICorDebugRegisterSet`目前可用。</span><span class="sxs-lookup"><span data-stu-id="1c747-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="1c747-111">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="1c747-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="1c747-112">取得目前執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="1c747-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="1c747-113">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="1c747-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="1c747-114">未實作適用於.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="1c747-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="1c747-115">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="1c747-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="1c747-116">.NET Framework 2.0 中，未實作。</span><span class="sxs-lookup"><span data-stu-id="1c747-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c747-117">備註</span><span class="sxs-lookup"><span data-stu-id="1c747-117">Remarks</span></span>  
 <span data-ttu-id="1c747-118">`ICorDebugRegisterSet`介面支援僅 32 位元暫存器。</span><span class="sxs-lookup"><span data-stu-id="1c747-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="1c747-119">使用[ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)需要其他暫存器，例如 IA-64 平台上的介面。</span><span class="sxs-lookup"><span data-stu-id="1c747-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c747-120">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1c747-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c747-121">需求</span><span class="sxs-lookup"><span data-stu-id="1c747-121">Requirements</span></span>  
 <span data-ttu-id="1c747-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c747-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c747-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c747-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c747-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c747-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1c747-125">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="1c747-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c747-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c747-126">See also</span></span>

- [<span data-ttu-id="1c747-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1c747-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1c747-128">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="1c747-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
