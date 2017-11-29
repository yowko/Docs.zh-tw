---
title: ICorDebugILFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame
helpviewer_keywords: ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8d370fa971f698eb694127c72ff96499b85143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="07b66-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="07b66-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="07b66-103">表示 Microsoft intermediate language (MSIL) 程式碼的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="07b66-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="07b66-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="07b66-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07b66-105">方法</span><span class="sxs-lookup"><span data-stu-id="07b66-105">Methods</span></span>  
  
|<span data-ttu-id="07b66-106">方法</span><span class="sxs-lookup"><span data-stu-id="07b66-106">Method</span></span>|<span data-ttu-id="07b66-107">說明</span><span class="sxs-lookup"><span data-stu-id="07b66-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07b66-108">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="07b66-109">取得值，指出是否能夠安全地將指令指標設定至指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="07b66-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="07b66-110">EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="07b66-111">在這個框架中取得的引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="07b66-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="07b66-112">EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="07b66-113">取得在這個框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="07b66-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="07b66-114">GetArgument 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="07b66-115">在這個 MSIL 堆疊框架中取得指定的引數的值。</span><span class="sxs-lookup"><span data-stu-id="07b66-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="07b66-116">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="07b66-117">取得指令指標的值以及說明如何取得指令指標的值的位元組合值。</span><span class="sxs-lookup"><span data-stu-id="07b66-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="07b66-118">GetLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="07b66-119">從此 MSIL 堆疊框架中取得指定的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="07b66-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="07b66-120">GetStackDepth 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="07b66-121">未實作。</span><span class="sxs-lookup"><span data-stu-id="07b66-121">Not implemented.</span></span>|  
|[<span data-ttu-id="07b66-122">GetStackValue 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="07b66-123">未實作。</span><span class="sxs-lookup"><span data-stu-id="07b66-123">Not implemented.</span></span>|  
|[<span data-ttu-id="07b66-124">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="07b66-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="07b66-125">將指令指標設定為 MSIL 程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="07b66-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07b66-126">備註</span><span class="sxs-lookup"><span data-stu-id="07b66-126">Remarks</span></span>  
 <span data-ttu-id="07b66-127">`ICorDebugILFrame`介面是特殊的 ICorDebugFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="07b66-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="07b66-128">它用 MSIL 程式碼框架，或在 just-in-time (JIT) 編譯的框架。</span><span class="sxs-lookup"><span data-stu-id="07b66-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="07b66-129">JIT 編譯的框架會同時實作`ICorDebugILFrame`介面和 ICorDebugNativeFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="07b66-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07b66-130">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="07b66-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07b66-131">需求</span><span class="sxs-lookup"><span data-stu-id="07b66-131">Requirements</span></span>  
 <span data-ttu-id="07b66-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07b66-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07b66-133">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07b66-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07b66-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07b66-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07b66-135">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07b66-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b66-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07b66-136">See Also</span></span>  
 [<span data-ttu-id="07b66-137">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="07b66-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
