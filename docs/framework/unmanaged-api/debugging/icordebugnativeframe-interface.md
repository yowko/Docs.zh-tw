---
title: ICorDebugNativeFrame Interface1
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
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: edd49d745be9db0c4c5309cf5febc3ff651a860f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="4c2bc-102">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="4c2bc-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="4c2bc-103">ICorDebugFrame 用於原生框架的特殊的實作。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c2bc-104">方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-104">Methods</span></span>  
  
|<span data-ttu-id="4c2bc-105">方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-105">Method</span></span>|<span data-ttu-id="4c2bc-106">描述</span><span class="sxs-lookup"><span data-stu-id="4c2bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c2bc-107">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="4c2bc-108">取得值，指出是否安全指令指標設在原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="4c2bc-109">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="4c2bc-110">取得原生程式碼中堆疊框架的位移。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="4c2bc-111">GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="4c2bc-112">取得表示的引數或兩個原生框架記憶體暫存器中儲存的本機變數的值 ICorDebugValue 指標。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="4c2bc-113">GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="4c2bc-114">取得指標`ICorDebugValue`，代表本機變數，其中的低位元會儲存在指定的暫存器和高的位元會儲存在指定的記憶體位址的值。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="4c2bc-115">GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="4c2bc-116">取得指標`ICorDebugValue`表示儲存在指定的記憶體位址變數的值。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="4c2bc-117">GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="4c2bc-118">取得指標`ICorDebugValue`，代表本機變數，其中高的位元會儲存在指定的暫存器和低位元會儲存在指定的記憶體位址的值</span><span class="sxs-lookup"><span data-stu-id="4c2bc-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="4c2bc-119">GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="4c2bc-120">取得指標`ICorDebugValue`表示的引數，或是儲存在指定的原生暫存器中的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="4c2bc-121">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="4c2bc-122">取得指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) ，代表這個設定的暫存器`ICorDebugNativeFrame`。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="4c2bc-123">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="4c2bc-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="4c2bc-124">將指定的位移位置的指令指標原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c2bc-125">備註</span><span class="sxs-lookup"><span data-stu-id="4c2bc-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c2bc-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c2bc-127">需求</span><span class="sxs-lookup"><span data-stu-id="4c2bc-127">Requirements</span></span>  
 <span data-ttu-id="4c2bc-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c2bc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c2bc-129">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c2bc-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c2bc-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c2bc-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c2bc-131">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c2bc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2bc-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c2bc-132">See Also</span></span>  
 [<span data-ttu-id="4c2bc-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4c2bc-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
