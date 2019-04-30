---
title: ICorDebugThread::CreateEval 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2016795e7b2c0588e2bd69e764fb96f7f90b24d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994067"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="b0a8f-102">ICorDebugThread::CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="b0a8f-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="b0a8f-103">建立 ICorDebugEval 物件會收集及公開此 ICorDebugThread 的功能。</span><span class="sxs-lookup"><span data-stu-id="b0a8f-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0a8f-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0a8f-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0a8f-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="b0a8f-106">[out]位址指標`ICorDebugEval`會收集並公開的功能，此執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="b0a8f-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0a8f-107">備註</span><span class="sxs-lookup"><span data-stu-id="b0a8f-107">Remarks</span></span>  
 <span data-ttu-id="b0a8f-108">評估物件會將推送新鏈結的執行緒上才能執行其運算。</span><span class="sxs-lookup"><span data-stu-id="b0a8f-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="b0a8f-109">這會中斷目前正在執行的執行緒上評估完成之前的計算。</span><span class="sxs-lookup"><span data-stu-id="b0a8f-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0a8f-110">需求</span><span class="sxs-lookup"><span data-stu-id="b0a8f-110">Requirements</span></span>  
 <span data-ttu-id="b0a8f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0a8f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a8f-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0a8f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0a8f-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0a8f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0a8f-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
