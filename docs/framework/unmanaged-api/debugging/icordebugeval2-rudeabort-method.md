---
title: ICorDebugEval2::RudeAbort 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: 478772925dfb7ca7389b5267433f9b06ace3d5a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729612"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="8277d-102">ICorDebugEval2::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="8277d-102">ICorDebugEval2::RudeAbort Method</span></span>

<span data-ttu-id="8277d-103">中止目前正在執行的計算 `ICorDebugEval2` 。</span><span class="sxs-lookup"><span data-stu-id="8277d-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8277d-104">語法</span><span class="sxs-lookup"><span data-stu-id="8277d-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8277d-105">備註</span><span class="sxs-lookup"><span data-stu-id="8277d-105">Remarks</span></span>  

 <span data-ttu-id="8277d-106">`RudeAbort` 不會釋放評估工具所持有的任何鎖定，因此它會讓偵錯工具保持不安全的狀態。</span><span class="sxs-lookup"><span data-stu-id="8277d-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="8277d-107">請特別小心呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="8277d-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8277d-108">需求</span><span class="sxs-lookup"><span data-stu-id="8277d-108">Requirements</span></span>  

 <span data-ttu-id="8277d-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8277d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8277d-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8277d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8277d-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8277d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8277d-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8277d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
