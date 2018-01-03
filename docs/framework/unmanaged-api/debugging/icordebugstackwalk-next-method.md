---
title: "ICorDebugStackWalk::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.Next Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a776f215d67c381a1c08416927cabd3ccb40afa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="be599-102">ICorDebugStackWalk::Next 方法</span><span class="sxs-lookup"><span data-stu-id="be599-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="be599-103">移動[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)下一個畫面格的物件。</span><span class="sxs-lookup"><span data-stu-id="be599-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be599-104">語法</span><span class="sxs-lookup"><span data-stu-id="be599-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="be599-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="be599-105">Return Value</span></span>  
 <span data-ttu-id="be599-106">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="be599-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="be599-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be599-107">HRESULT</span></span>|<span data-ttu-id="be599-108">描述</span><span class="sxs-lookup"><span data-stu-id="be599-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be599-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="be599-109">S_OK</span></span>|<span data-ttu-id="be599-110">執行階段成功回溯至下一個畫面格 （請參閱 < 備註 >）。</span><span class="sxs-lookup"><span data-stu-id="be599-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="be599-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be599-111">E_FAIL</span></span>|<span data-ttu-id="be599-112">`ICorDebugStackWalk`物件不可以進階。</span><span class="sxs-lookup"><span data-stu-id="be599-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="be599-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="be599-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="be599-114">由於此回溯已到達堆疊的結尾。</span><span class="sxs-lookup"><span data-stu-id="be599-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="be599-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="be599-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="be599-116">框架指標已經結尾的堆疊。因此，沒有其他框架則可以存取。</span><span class="sxs-lookup"><span data-stu-id="be599-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="be599-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="be599-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be599-118">備註</span><span class="sxs-lookup"><span data-stu-id="be599-118">Remarks</span></span>  
 <span data-ttu-id="be599-119">`Next`方法往前移`ICorDebugStackWalk`物件呼叫框架，只有當執行階段可以回溯目前的框架。</span><span class="sxs-lookup"><span data-stu-id="be599-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="be599-120">否則，物件前進至下一步，執行階段可以回溯框架。</span><span class="sxs-lookup"><span data-stu-id="be599-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be599-121">需求</span><span class="sxs-lookup"><span data-stu-id="be599-121">Requirements</span></span>  
 <span data-ttu-id="be599-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be599-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be599-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be599-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be599-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be599-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be599-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be599-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be599-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="be599-126">See Also</span></span>  
 [<span data-ttu-id="be599-127">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="be599-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="be599-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="be599-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="be599-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="be599-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
