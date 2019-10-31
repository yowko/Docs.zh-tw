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
ms.openlocfilehash: 0c622e0eba27f501446d2b7d9d264ee0834e869c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133623"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="f2e0b-102">ICorDebugThread::CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="f2e0b-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="f2e0b-103">建立 ICorDebugEval 物件，它會收集並公開此 ICorDebugThread 的功能。</span><span class="sxs-lookup"><span data-stu-id="f2e0b-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e0b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2e0b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2e0b-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2e0b-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="f2e0b-106">脫銷收集並公開這個執行緒之功能的 `ICorDebugEval` 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="f2e0b-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2e0b-107">備註</span><span class="sxs-lookup"><span data-stu-id="f2e0b-107">Remarks</span></span>  
 <span data-ttu-id="f2e0b-108">評估物件會先線上程上推送新的鏈，再進行其計算。</span><span class="sxs-lookup"><span data-stu-id="f2e0b-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="f2e0b-109">這會中斷目前正線上程上執行的計算，直到評估完成為止。</span><span class="sxs-lookup"><span data-stu-id="f2e0b-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2e0b-110">需求</span><span class="sxs-lookup"><span data-stu-id="f2e0b-110">Requirements</span></span>  
 <span data-ttu-id="f2e0b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e0b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2e0b-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2e0b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2e0b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2e0b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2e0b-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2e0b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
