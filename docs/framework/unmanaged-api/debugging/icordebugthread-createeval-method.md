---
title: "ICorDebugThread::CreateEval 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 766677d9eef60c811c8537bc60bb8db29dd988c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="99f29-102">ICorDebugThread::CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="99f29-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="99f29-103">建立會收集及公開功能的這個 ICorDebugThread ICorDebugEval 物件。</span><span class="sxs-lookup"><span data-stu-id="99f29-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99f29-104">語法</span><span class="sxs-lookup"><span data-stu-id="99f29-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99f29-105">參數</span><span class="sxs-lookup"><span data-stu-id="99f29-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="99f29-106">[out]位址指標`ICorDebugEval`物件，會收集並公開這個執行緒的功能。</span><span class="sxs-lookup"><span data-stu-id="99f29-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99f29-107">備註</span><span class="sxs-lookup"><span data-stu-id="99f29-107">Remarks</span></span>  
 <span data-ttu-id="99f29-108">評估物件會將推送新鏈結的執行緒上執行其計算之前。</span><span class="sxs-lookup"><span data-stu-id="99f29-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="99f29-109">這會中斷目前正在執行的執行緒上評估完成之前的計算。</span><span class="sxs-lookup"><span data-stu-id="99f29-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99f29-110">需求</span><span class="sxs-lookup"><span data-stu-id="99f29-110">Requirements</span></span>  
 <span data-ttu-id="99f29-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99f29-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99f29-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99f29-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99f29-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99f29-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99f29-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99f29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
