---
title: ICorDebugILFrame 介面 1
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
ms.openlocfilehash: 73cf7f26b228fa5aa458a6de312df3bf777e0206
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580508"
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="3e949-102">ICorDebugILFrame 介面 1</span><span class="sxs-lookup"><span data-stu-id="3e949-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="3e949-103">表示 Microsoft intermediate language (MSIL) 程式碼的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="3e949-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="3e949-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="3e949-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e949-105">方法</span><span class="sxs-lookup"><span data-stu-id="3e949-105">Methods</span></span>  
  
|<span data-ttu-id="3e949-106">方法</span><span class="sxs-lookup"><span data-stu-id="3e949-106">Method</span></span>|<span data-ttu-id="3e949-107">描述</span><span class="sxs-lookup"><span data-stu-id="3e949-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e949-108">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="3e949-109">取得值，指出是否將指令指標設定為指定的位移位置的安全。</span><span class="sxs-lookup"><span data-stu-id="3e949-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="3e949-110">EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="3e949-111">取得列舉值的引數，這個框架中。</span><span class="sxs-lookup"><span data-stu-id="3e949-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="3e949-112">EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="3e949-113">取得這個框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="3e949-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="3e949-114">GetArgument 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="3e949-115">在此 MSIL 堆疊框架中取得指定的引數的值。</span><span class="sxs-lookup"><span data-stu-id="3e949-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="3e949-116">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="3e949-117">取得指令指標的值和描述如何取得指令指標的值的位元組合值。</span><span class="sxs-lookup"><span data-stu-id="3e949-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="3e949-118">GetLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="3e949-119">在此 MSIL 堆疊框架中取得指定的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="3e949-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="3e949-120">GetStackDepth 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="3e949-121">未實作。</span><span class="sxs-lookup"><span data-stu-id="3e949-121">Not implemented.</span></span>|  
|[<span data-ttu-id="3e949-122">GetStackValue 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="3e949-123">未實作。</span><span class="sxs-lookup"><span data-stu-id="3e949-123">Not implemented.</span></span>|  
|[<span data-ttu-id="3e949-124">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="3e949-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="3e949-125">將指令指標設定為 MSIL 程式碼中指定的位移位置中。</span><span class="sxs-lookup"><span data-stu-id="3e949-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e949-126">備註</span><span class="sxs-lookup"><span data-stu-id="3e949-126">Remarks</span></span>  
 <span data-ttu-id="3e949-127">`ICorDebugILFrame`介面是特製化的 ICorDebugFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="3e949-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="3e949-128">它使用 MSIL 程式碼框架，或在 just-in-time (JIT) 編譯的框架。</span><span class="sxs-lookup"><span data-stu-id="3e949-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="3e949-129">JIT 編譯的畫面格同時實作`ICorDebugILFrame`介面和 ICorDebugNativeFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="3e949-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e949-130">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="3e949-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e949-131">需求</span><span class="sxs-lookup"><span data-stu-id="3e949-131">Requirements</span></span>  
 <span data-ttu-id="3e949-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e949-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e949-133">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e949-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e949-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e949-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e949-135">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e949-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e949-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e949-136">See also</span></span>
- [<span data-ttu-id="3e949-137">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3e949-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
