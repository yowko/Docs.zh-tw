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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988919"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="72623-102">ICorDebugEval2::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="72623-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="72623-103">中止計算這個`ICorDebugEval2`目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="72623-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72623-104">語法</span><span class="sxs-lookup"><span data-stu-id="72623-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="72623-105">備註</span><span class="sxs-lookup"><span data-stu-id="72623-105">Remarks</span></span>  
 <span data-ttu-id="72623-106">`RudeAbort` 不會釋放評估工具會保留任何鎖定，因此在不安全的狀態不會留下偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="72623-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="72623-107">呼叫這個方法時應謹慎小心。</span><span class="sxs-lookup"><span data-stu-id="72623-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72623-108">需求</span><span class="sxs-lookup"><span data-stu-id="72623-108">Requirements</span></span>  
 <span data-ttu-id="72623-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72623-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72623-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72623-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72623-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72623-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72623-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72623-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
