---
title: ICorDebugNativeFrame 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994613"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="67c16-102">ICorDebugNativeFrame 介面</span><span class="sxs-lookup"><span data-stu-id="67c16-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="67c16-103">ICorDebugFrame 用於原生框架的特殊的實作。</span><span class="sxs-lookup"><span data-stu-id="67c16-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67c16-104">方法</span><span class="sxs-lookup"><span data-stu-id="67c16-104">Methods</span></span>  
  
|<span data-ttu-id="67c16-105">方法</span><span class="sxs-lookup"><span data-stu-id="67c16-105">Method</span></span>|<span data-ttu-id="67c16-106">描述</span><span class="sxs-lookup"><span data-stu-id="67c16-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67c16-107">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="67c16-108">取得值，指出它是否安全地在機器碼中設定指令指標至指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="67c16-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="67c16-109">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="67c16-110">取得原生程式碼的堆疊框架的位移。</span><span class="sxs-lookup"><span data-stu-id="67c16-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="67c16-111">GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="67c16-112">取得表示引數或儲存在兩個記憶體暫存器的原生框架中的本機變數的值 ICorDebugValue 的指標。</span><span class="sxs-lookup"><span data-stu-id="67c16-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="67c16-113">GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="67c16-114">取得指標`ICorDebugValue`，代表本機變數，其中的低位元會儲存在指定的暫存器，以及高的位元會儲存在指定的記憶體位址的值。</span><span class="sxs-lookup"><span data-stu-id="67c16-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="67c16-115">GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="67c16-116">取得指標`ICorDebugValue`，代表儲存在指定的記憶體位址的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="67c16-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="67c16-117">GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="67c16-118">取得指標`ICorDebugValue`，代表本機變數，其中的高的位元會儲存在指定的暫存器，和低的位元會儲存在指定的記憶體位址的值</span><span class="sxs-lookup"><span data-stu-id="67c16-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="67c16-119">GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="67c16-120">取得指標`ICorDebugValue`表示引數或儲存在指定的原生暫存器的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="67c16-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="67c16-121">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="67c16-122">取得指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) ，表示此設定的暫存器`ICorDebugNativeFrame`。</span><span class="sxs-lookup"><span data-stu-id="67c16-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="67c16-123">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="67c16-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="67c16-124">指令指標設定為原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="67c16-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67c16-125">備註</span><span class="sxs-lookup"><span data-stu-id="67c16-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67c16-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="67c16-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67c16-127">需求</span><span class="sxs-lookup"><span data-stu-id="67c16-127">Requirements</span></span>  
 <span data-ttu-id="67c16-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67c16-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67c16-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67c16-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67c16-130">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67c16-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67c16-131">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67c16-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c16-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67c16-132">See also</span></span>

- [<span data-ttu-id="67c16-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="67c16-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
