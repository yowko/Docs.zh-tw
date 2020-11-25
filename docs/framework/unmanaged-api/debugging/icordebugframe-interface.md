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
ms.openlocfilehash: bdc17e2c6c63deae1420fe738eac51153f6b368e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726336"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="74231-102">ICorDebugFrame 介面</span><span class="sxs-lookup"><span data-stu-id="74231-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="74231-103">表示目前堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="74231-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74231-104">方法</span><span class="sxs-lookup"><span data-stu-id="74231-104">Methods</span></span>  
  
|<span data-ttu-id="74231-105">方法</span><span class="sxs-lookup"><span data-stu-id="74231-105">Method</span></span>|<span data-ttu-id="74231-106">描述</span><span class="sxs-lookup"><span data-stu-id="74231-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74231-107">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="74231-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="74231-108">取得 ICorDebugStepper，以執行與此相關的逐步執行作業 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="74231-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="74231-109">GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="74231-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="74231-110">取得 `ICorDebugFrame` 此框架所呼叫之目前鏈中的指標，如果這是鏈中最內層的框架，則傳回 null。</span><span class="sxs-lookup"><span data-stu-id="74231-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="74231-111">GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="74231-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="74231-112">取得 `ICorDebugFrame` 目前鏈中呼叫此框架的指標，如果這是鏈中最外層的框架，則會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="74231-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="74231-113">GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="74231-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="74231-114">取得此所屬 ICorDebugChain 的指標 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="74231-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="74231-115">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="74231-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="74231-116">取得與此堆疊框架相關聯之 ICorDebugCode 的指標。</span><span class="sxs-lookup"><span data-stu-id="74231-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="74231-117">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="74231-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="74231-118">取得 ICorDebugFunction 的指標，其中包含與此堆疊框架相關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="74231-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="74231-119">GetFunctionToken 方法</span><span class="sxs-lookup"><span data-stu-id="74231-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="74231-120">取得函式的元資料標記，該函式包含與這個堆疊框架相關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="74231-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="74231-121">GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="74231-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="74231-122">取得這個所表示之堆疊框架的絕對位址範圍 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="74231-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74231-123">備註</span><span class="sxs-lookup"><span data-stu-id="74231-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74231-124">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="74231-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74231-125">需求</span><span class="sxs-lookup"><span data-stu-id="74231-125">Requirements</span></span>  

 <span data-ttu-id="74231-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74231-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74231-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74231-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74231-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74231-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74231-129">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74231-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74231-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74231-130">See also</span></span>

- [<span data-ttu-id="74231-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="74231-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
