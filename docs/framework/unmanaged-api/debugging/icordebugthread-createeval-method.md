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
ms.openlocfilehash: 1c0037530ae4f40be5bef4da8f398afe5f2bbb91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688285"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="99597-102">ICorDebugThread::CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="99597-102">ICorDebugThread::CreateEval Method</span></span>

<span data-ttu-id="99597-103">建立 ICorDebugEval 物件，此物件會收集並公開此 ICorDebugThread 的功能。</span><span class="sxs-lookup"><span data-stu-id="99597-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99597-104">語法</span><span class="sxs-lookup"><span data-stu-id="99597-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99597-105">參數</span><span class="sxs-lookup"><span data-stu-id="99597-105">Parameters</span></span>  

 `ppEval`  
 <span data-ttu-id="99597-106">擴展物件位址的指標， `ICorDebugEval` 該物件會收集並公開這個執行緒的功能。</span><span class="sxs-lookup"><span data-stu-id="99597-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99597-107">備註</span><span class="sxs-lookup"><span data-stu-id="99597-107">Remarks</span></span>  

 <span data-ttu-id="99597-108">評估物件會在執行其計算之前，線上程上推送新的鏈。</span><span class="sxs-lookup"><span data-stu-id="99597-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="99597-109">這會中斷目前線上程上執行的計算，直到評估完成為止。</span><span class="sxs-lookup"><span data-stu-id="99597-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99597-110">需求</span><span class="sxs-lookup"><span data-stu-id="99597-110">Requirements</span></span>  

 <span data-ttu-id="99597-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99597-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99597-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99597-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99597-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99597-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99597-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99597-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
