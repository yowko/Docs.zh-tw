---
title: ICorDebugFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209613"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="d8ee8-102">ICorDebugFrame 介面</span><span class="sxs-lookup"><span data-stu-id="d8ee8-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="d8ee8-103">表示目前堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8ee8-104">方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-104">Methods</span></span>  
  
|<span data-ttu-id="d8ee8-105">方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-105">Method</span></span>|<span data-ttu-id="d8ee8-106">描述</span><span class="sxs-lookup"><span data-stu-id="d8ee8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8ee8-107">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="d8ee8-108">取得 ICorDebugStepper，以執行相對於這個的逐步操作 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="d8ee8-109">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="d8ee8-110">取得 `ICorDebugFrame` 此框架所呼叫之目前鏈中的指標，如果這是鏈中最內層的框架，則會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="d8ee8-111">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="d8ee8-112">取得 `ICorDebugFrame` 目前鏈中呼叫此框架的指標，如果這是鏈中最外層的框架，則會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="d8ee8-113">GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="d8ee8-114">取得此所屬 ICorDebugChain 的指標 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="d8ee8-115">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="d8ee8-116">取得與這個堆疊框架相關聯之 ICorDebugCode 的指標。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="d8ee8-117">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="d8ee8-118">取得 ICorDebugFunction 的指標，其中包含與這個堆疊框架相關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="d8ee8-119">GetFunctionToken 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="d8ee8-120">取得包含與此堆疊框架相關聯之程式碼的函式的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="d8ee8-121">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="d8ee8-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="d8ee8-122">取得這個所表示之堆疊框架的絕對位址範圍 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8ee8-123">備註</span><span class="sxs-lookup"><span data-stu-id="d8ee8-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8ee8-124">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ee8-125">需求</span><span class="sxs-lookup"><span data-stu-id="d8ee8-125">Requirements</span></span>  
 <span data-ttu-id="d8ee8-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ee8-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ee8-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ee8-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ee8-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ee8-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ee8-129">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ee8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ee8-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ee8-130">See also</span></span>

- [<span data-ttu-id="d8ee8-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d8ee8-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
