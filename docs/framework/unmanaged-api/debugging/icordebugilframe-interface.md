---
title: ICorDebugILFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a40436fcf1485c5d08d175b0396af2b6870c19a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917026"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="1a77d-102">ICorDebugILFrame 介面</span><span class="sxs-lookup"><span data-stu-id="1a77d-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="1a77d-103">表示 Microsoft 中繼語言 (MSIL) 程式碼的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="1a77d-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="1a77d-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="1a77d-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a77d-105">方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-105">Methods</span></span>  
  
|<span data-ttu-id="1a77d-106">方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-106">Method</span></span>|<span data-ttu-id="1a77d-107">說明</span><span class="sxs-lookup"><span data-stu-id="1a77d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a77d-108">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="1a77d-109">取得值, 指出是否可以安全地將指令指標設定為指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="1a77d-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="1a77d-110">EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="1a77d-111">取得此框架中引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1a77d-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="1a77d-112">EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="1a77d-113">取得此框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1a77d-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="1a77d-114">GetArgument 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="1a77d-115">取得這個 MSIL 堆疊框架中指定之引數的值。</span><span class="sxs-lookup"><span data-stu-id="1a77d-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="1a77d-116">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="1a77d-117">取得指令指標的值, 以及描述如何取得指令指標值的位組合值。</span><span class="sxs-lookup"><span data-stu-id="1a77d-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="1a77d-118">GetLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="1a77d-119">取得這個 MSIL 堆疊框架中指定之區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="1a77d-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="1a77d-120">GetStackDepth 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="1a77d-121">未實作。</span><span class="sxs-lookup"><span data-stu-id="1a77d-121">Not implemented.</span></span>|  
|[<span data-ttu-id="1a77d-122">GetStackValue 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="1a77d-123">未實作。</span><span class="sxs-lookup"><span data-stu-id="1a77d-123">Not implemented.</span></span>|  
|[<span data-ttu-id="1a77d-124">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="1a77d-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="1a77d-125">將指令指標設定為 MSIL 程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="1a77d-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a77d-126">備註</span><span class="sxs-lookup"><span data-stu-id="1a77d-126">Remarks</span></span>  
 <span data-ttu-id="1a77d-127">`ICorDebugILFrame`介面是特製化的 ICorDebugFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="1a77d-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="1a77d-128">它可用於 MSIL 程式碼框架或即時 (JIT) 編譯的框架。</span><span class="sxs-lookup"><span data-stu-id="1a77d-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="1a77d-129">JIT 編譯的框架會同時`ICorDebugILFrame`執行介面和 ICorDebugNativeFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="1a77d-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a77d-130">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1a77d-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a77d-131">需求</span><span class="sxs-lookup"><span data-stu-id="1a77d-131">Requirements</span></span>  
 <span data-ttu-id="1a77d-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1a77d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a77d-133">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a77d-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a77d-134">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a77d-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a77d-135">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a77d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a77d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a77d-136">See also</span></span>

- [<span data-ttu-id="1a77d-137">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1a77d-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
