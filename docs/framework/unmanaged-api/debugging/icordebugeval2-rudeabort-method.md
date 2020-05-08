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
ms.openlocfilehash: e901c65824ee8d6949c79c7778944148c0d9eb28
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976053"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="fe481-102">ICorDebugEval2::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="fe481-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="fe481-103">中止目前正在執行的`ICorDebugEval2`計算。</span><span class="sxs-lookup"><span data-stu-id="fe481-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe481-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe481-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fe481-105">備註</span><span class="sxs-lookup"><span data-stu-id="fe481-105">Remarks</span></span>  
 <span data-ttu-id="fe481-106">`RudeAbort`不會釋放評估工具所持有的任何鎖定，因此它會讓偵錯工具保持不安全的狀態。</span><span class="sxs-lookup"><span data-stu-id="fe481-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="fe481-107">請特別小心呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="fe481-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe481-108">需求</span><span class="sxs-lookup"><span data-stu-id="fe481-108">Requirements</span></span>  
 <span data-ttu-id="fe481-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe481-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe481-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe481-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe481-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe481-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe481-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe481-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
