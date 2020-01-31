---
title: ICorDebugStackWalk::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: b76d17337408653d130ee0cb8594e759bdade37c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791873"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="e42ff-102">ICorDebugStackWalk::Next 方法</span><span class="sxs-lookup"><span data-stu-id="e42ff-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="e42ff-103">將[ICorDebugStackWalk](icordebugstackwalk-interface.md)物件移至下一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="e42ff-103">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="e42ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e42ff-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="e42ff-105">Return Value</span></span>  
 <span data-ttu-id="e42ff-106">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="e42ff-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e42ff-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e42ff-107">HRESULT</span></span>|<span data-ttu-id="e42ff-108">描述</span><span class="sxs-lookup"><span data-stu-id="e42ff-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e42ff-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="e42ff-109">S_OK</span></span>|<span data-ttu-id="e42ff-110">執行時間已成功地向下一個畫面格展開（請參閱備註）。</span><span class="sxs-lookup"><span data-stu-id="e42ff-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="e42ff-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e42ff-111">E_FAIL</span></span>|<span data-ttu-id="e42ff-112">無法將 `ICorDebugStackWalk` 物件 advanced。</span><span class="sxs-lookup"><span data-stu-id="e42ff-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="e42ff-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="e42ff-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="e42ff-114">因為這個回溯的結果，所以已達到堆疊的結尾。</span><span class="sxs-lookup"><span data-stu-id="e42ff-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="e42ff-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="e42ff-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="e42ff-116">框架指標已在堆疊的結尾;因此，不能存取任何其他框架。</span><span class="sxs-lookup"><span data-stu-id="e42ff-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e42ff-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="e42ff-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e42ff-118">備註</span><span class="sxs-lookup"><span data-stu-id="e42ff-118">Remarks</span></span>  
 <span data-ttu-id="e42ff-119">只有當執行時間可以回溯目前的框架時，`Next` 方法才會將 `ICorDebugStackWalk` 物件前移至呼叫的框架。</span><span class="sxs-lookup"><span data-stu-id="e42ff-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="e42ff-120">否則，物件會前進到執行時間可以回溯的下一個框架。</span><span class="sxs-lookup"><span data-stu-id="e42ff-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e42ff-121">需求</span><span class="sxs-lookup"><span data-stu-id="e42ff-121">Requirements</span></span>  
 <span data-ttu-id="e42ff-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e42ff-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e42ff-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e42ff-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e42ff-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e42ff-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e42ff-125">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e42ff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42ff-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="e42ff-126">See also</span></span>

- [<span data-ttu-id="e42ff-127">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="e42ff-127">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="e42ff-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e42ff-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e42ff-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="e42ff-129">Debugging</span></span>](index.md)
