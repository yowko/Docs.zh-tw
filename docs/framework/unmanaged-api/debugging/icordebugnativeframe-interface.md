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
ms.openlocfilehash: 043dc0fdd5218d7bc6b80428d1eb891b3f01ee8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695513"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="7d5c9-102">ICorDebugNativeFrame 介面</span><span class="sxs-lookup"><span data-stu-id="7d5c9-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="7d5c9-103">用於原生框架的 ICorDebugFrame 專用實作為。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d5c9-104">方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-104">Methods</span></span>  
  
|<span data-ttu-id="7d5c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-105">Method</span></span>|<span data-ttu-id="7d5c9-106">描述</span><span class="sxs-lookup"><span data-stu-id="7d5c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d5c9-107">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="7d5c9-108">取得值，這個值會指出是否可以安全地將指令指標設定為原生程式碼中的指定位移位置。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="7d5c9-109">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="7d5c9-110">取得原生程式碼的堆疊框架位移。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="7d5c9-111">GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="7d5c9-112">取得 ICorDebugValue 的指標，該指標表示儲存在原生框架之兩個記憶體暫存器中的引數或區域變數值。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="7d5c9-113">GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="7d5c9-114">取得 `ICorDebugValue` 代表區域變數值的指標，該變數的低位會儲存在指定的暫存器中，而且會在指定的記憶體位址儲存高位。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="7d5c9-115">GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="7d5c9-116">取得的指標 `ICorDebugValue` ，該指標表示儲存在指定之記憶體位址的本機變數值。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="7d5c9-117">GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="7d5c9-118">取得 `ICorDebugValue` 代表區域變數值的指標，該變數的最高位儲存在指定的暫存器中，而低位儲存在指定的記憶體位址</span><span class="sxs-lookup"><span data-stu-id="7d5c9-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="7d5c9-119">GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="7d5c9-120">取得的指標 `ICorDebugValue` ，代表所指定原生暫存器中所儲存之引數或區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="7d5c9-121">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="7d5c9-122">取得 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 的指標，該指標表示這個的註冊集 `ICorDebugNativeFrame` 。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="7d5c9-123">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="7d5c9-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="7d5c9-124">將指令指標設定為原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d5c9-125">備註</span><span class="sxs-lookup"><span data-stu-id="7d5c9-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d5c9-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d5c9-127">需求</span><span class="sxs-lookup"><span data-stu-id="7d5c9-127">Requirements</span></span>  

 <span data-ttu-id="7d5c9-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d5c9-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d5c9-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d5c9-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d5c9-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d5c9-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d5c9-131">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d5c9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5c9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d5c9-132">See also</span></span>

- [<span data-ttu-id="7d5c9-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7d5c9-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
