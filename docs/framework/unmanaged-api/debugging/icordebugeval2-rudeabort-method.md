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
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084789"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="e5dd5-102">ICorDebugEval2::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="e5dd5-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="e5dd5-103">中止此 `ICorDebugEval2` 目前正在執行的計算。</span><span class="sxs-lookup"><span data-stu-id="e5dd5-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5dd5-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5dd5-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e5dd5-105">備註</span><span class="sxs-lookup"><span data-stu-id="e5dd5-105">Remarks</span></span>  
 <span data-ttu-id="e5dd5-106">`RudeAbort` 不會釋放評估工具所持有的任何鎖定，因此它會讓偵錯工具保持不安全的狀態。</span><span class="sxs-lookup"><span data-stu-id="e5dd5-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="e5dd5-107">請特別小心呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="e5dd5-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5dd5-108">需求</span><span class="sxs-lookup"><span data-stu-id="e5dd5-108">Requirements</span></span>  
 <span data-ttu-id="e5dd5-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5dd5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5dd5-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5dd5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5dd5-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5dd5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5dd5-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5dd5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
