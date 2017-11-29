---
title: ICorDebugNativeFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 63d631dec00e63d6ee383cd36d79382a529d9ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="aefca-102">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="aefca-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="aefca-103">ICorDebugFrame 用於原生框架的特殊的實作。</span><span class="sxs-lookup"><span data-stu-id="aefca-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aefca-104">方法</span><span class="sxs-lookup"><span data-stu-id="aefca-104">Methods</span></span>  
  
|<span data-ttu-id="aefca-105">方法</span><span class="sxs-lookup"><span data-stu-id="aefca-105">Method</span></span>|<span data-ttu-id="aefca-106">說明</span><span class="sxs-lookup"><span data-stu-id="aefca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aefca-107">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="aefca-108">取得值，指出是否安全指令指標設在原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="aefca-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="aefca-109">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="aefca-110">取得原生程式碼中堆疊框架的位移。</span><span class="sxs-lookup"><span data-stu-id="aefca-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="aefca-111">GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="aefca-112">取得表示的引數或兩個原生框架記憶體暫存器中儲存的本機變數的值 ICorDebugValue 指標。</span><span class="sxs-lookup"><span data-stu-id="aefca-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="aefca-113">GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="aefca-114">取得指標`ICorDebugValue`，代表本機變數，其中的低位元會儲存在指定的暫存器和高的位元會儲存在指定的記憶體位址的值。</span><span class="sxs-lookup"><span data-stu-id="aefca-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="aefca-115">GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="aefca-116">取得指標`ICorDebugValue`表示儲存在指定的記憶體位址變數的值。</span><span class="sxs-lookup"><span data-stu-id="aefca-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="aefca-117">GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="aefca-118">取得指標`ICorDebugValue`，代表本機變數，其中高的位元會儲存在指定的暫存器和低位元會儲存在指定的記憶體位址的值</span><span class="sxs-lookup"><span data-stu-id="aefca-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="aefca-119">GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="aefca-120">取得指標`ICorDebugValue`表示的引數，或是儲存在指定的原生暫存器中的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="aefca-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="aefca-121">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="aefca-122">取得指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) ，代表這個設定的暫存器`ICorDebugNativeFrame`。</span><span class="sxs-lookup"><span data-stu-id="aefca-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="aefca-123">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="aefca-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="aefca-124">將指定的位移位置的指令指標原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="aefca-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aefca-125">備註</span><span class="sxs-lookup"><span data-stu-id="aefca-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aefca-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="aefca-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aefca-127">需求</span><span class="sxs-lookup"><span data-stu-id="aefca-127">Requirements</span></span>  
 <span data-ttu-id="aefca-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aefca-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aefca-129">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aefca-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aefca-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aefca-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aefca-131">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aefca-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefca-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aefca-132">See Also</span></span>  
 [<span data-ttu-id="aefca-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="aefca-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
