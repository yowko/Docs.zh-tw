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
ms.openlocfilehash: 7a27b8ec512498c7bf817aca36267c37d8070a4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788574"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="6581e-102">ICorDebugILFrame 介面</span><span class="sxs-lookup"><span data-stu-id="6581e-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="6581e-103">表示 Microsoft 中繼語言（MSIL）程式碼的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="6581e-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="6581e-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="6581e-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6581e-105">方法</span><span class="sxs-lookup"><span data-stu-id="6581e-105">Methods</span></span>  
  
|<span data-ttu-id="6581e-106">方法</span><span class="sxs-lookup"><span data-stu-id="6581e-106">Method</span></span>|<span data-ttu-id="6581e-107">描述</span><span class="sxs-lookup"><span data-stu-id="6581e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6581e-108">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="6581e-109">取得值，指出是否可以安全地將指令指標設定為指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="6581e-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="6581e-110">EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="6581e-111">取得此框架中引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="6581e-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="6581e-112">EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="6581e-113">取得此框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="6581e-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="6581e-114">GetArgument 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="6581e-115">取得這個 MSIL 堆疊框架中指定之引數的值。</span><span class="sxs-lookup"><span data-stu-id="6581e-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="6581e-116">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="6581e-117">取得指令指標的值，以及描述如何取得指令指標值的位組合值。</span><span class="sxs-lookup"><span data-stu-id="6581e-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="6581e-118">GetLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="6581e-119">取得這個 MSIL 堆疊框架中指定之區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="6581e-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="6581e-120">GetStackDepth 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="6581e-121">未實作。</span><span class="sxs-lookup"><span data-stu-id="6581e-121">Not implemented.</span></span>|  
|[<span data-ttu-id="6581e-122">GetStackValue 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="6581e-123">未實作。</span><span class="sxs-lookup"><span data-stu-id="6581e-123">Not implemented.</span></span>|  
|[<span data-ttu-id="6581e-124">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="6581e-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="6581e-125">將指令指標設定為 MSIL 程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="6581e-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6581e-126">備註</span><span class="sxs-lookup"><span data-stu-id="6581e-126">Remarks</span></span>  
 <span data-ttu-id="6581e-127">`ICorDebugILFrame` 介面是特製化的 ICorDebugFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="6581e-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="6581e-128">它可用於 MSIL 程式碼框架或即時（JIT）編譯的框架。</span><span class="sxs-lookup"><span data-stu-id="6581e-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="6581e-129">JIT 編譯的框架會同時執行 `ICorDebugILFrame` 介面和 ICorDebugNativeFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="6581e-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6581e-130">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6581e-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6581e-131">需求</span><span class="sxs-lookup"><span data-stu-id="6581e-131">Requirements</span></span>  
 <span data-ttu-id="6581e-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6581e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6581e-133">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6581e-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6581e-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6581e-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6581e-135">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6581e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6581e-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="6581e-136">See also</span></span>

- [<span data-ttu-id="6581e-137">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6581e-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
