---
title: ICorDebugFrame 介面 1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f160612e499ca7bd2185c95aa07a3784c5a4a19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635745"
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="7a5ef-102">ICorDebugFrame 介面 1</span><span class="sxs-lookup"><span data-stu-id="7a5ef-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="7a5ef-103">表示目前堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a5ef-104">方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-104">Methods</span></span>  
  
|<span data-ttu-id="7a5ef-105">方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-105">Method</span></span>|<span data-ttu-id="7a5ef-106">描述</span><span class="sxs-lookup"><span data-stu-id="7a5ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a5ef-107">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="7a5ef-108">取得執行逐步執行的作業，相對於這個 ICorDebugStepper `ICorDebugFrame`。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="7a5ef-109">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="7a5ef-110">取得指標`ICorDebugFrame`目前鏈結，呼叫此框架，或傳回 null，如果這是鏈結中最內層的框架中。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="7a5ef-111">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="7a5ef-112">取得指標`ICorDebugFrame`目前鏈結中，呼叫此框架中，或傳回 null，如果這個鏈結中最外層的框架。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="7a5ef-113">GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="7a5ef-114">取得變數的指標，ICorDebugChain 這個`ICorDebugFrame`是的一部分。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="7a5ef-115">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="7a5ef-116">取得此堆疊框架相關聯 ICorDebugCode 的指標。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="7a5ef-117">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="7a5ef-118">取得包含此堆疊框架相關聯的程式碼 ICorDebugFunction 的指標。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="7a5ef-119">GetFunctionToken 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="7a5ef-120">取得包含此堆疊框架相關聯的程式碼的函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="7a5ef-121">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="7a5ef-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="7a5ef-122">取得所表示的堆疊框架的絕對位址範圍`ICorDebugFrame`。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a5ef-123">備註</span><span class="sxs-lookup"><span data-stu-id="7a5ef-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a5ef-124">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a5ef-125">需求</span><span class="sxs-lookup"><span data-stu-id="7a5ef-125">Requirements</span></span>  
 <span data-ttu-id="7a5ef-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a5ef-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a5ef-127">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a5ef-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a5ef-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a5ef-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a5ef-129">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a5ef-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5ef-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a5ef-130">See also</span></span>
- [<span data-ttu-id="7a5ef-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7a5ef-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
