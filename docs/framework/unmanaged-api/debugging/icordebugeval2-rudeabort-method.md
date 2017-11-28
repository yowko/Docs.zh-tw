---
title: "ICorDebugEval2::RudeAbort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.RudeAbort
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1dd0d00338f3f9ff9ac63e84a29124913cc9febe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="05a2f-102">ICorDebugEval2::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="05a2f-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="05a2f-103">中止計算此`ICorDebugEval2`目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="05a2f-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a2f-104">語法</span><span class="sxs-lookup"><span data-stu-id="05a2f-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="05a2f-105">備註</span><span class="sxs-lookup"><span data-stu-id="05a2f-105">Remarks</span></span>  
 <span data-ttu-id="05a2f-106">`RudeAbort`不會釋放，評估工具會保存任何鎖定，因此會使偵錯工作階段處於不安全的狀態。</span><span class="sxs-lookup"><span data-stu-id="05a2f-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="05a2f-107">呼叫這個方法時應謹慎小心。</span><span class="sxs-lookup"><span data-stu-id="05a2f-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05a2f-108">需求</span><span class="sxs-lookup"><span data-stu-id="05a2f-108">Requirements</span></span>  
 <span data-ttu-id="05a2f-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05a2f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a2f-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05a2f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05a2f-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05a2f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05a2f-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a2f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
