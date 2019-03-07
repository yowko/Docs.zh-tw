---
title: ICorDebugThread::GetCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4baa4eb4da48b923ab0137ca25d9d819c94e33d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487339"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="3150d-102">ICorDebugThread::GetCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="3150d-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="3150d-103">ICorDebugValue 物件，表示目前正在 managed 程式碼所擲回例外狀況取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="3150d-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3150d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3150d-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3150d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3150d-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="3150d-106">[out]位址指標`ICorDebugValue`物件，表示目前所所擲回的例外狀況的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="3150d-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3150d-107">備註</span><span class="sxs-lookup"><span data-stu-id="3150d-107">Remarks</span></span>  
 <span data-ttu-id="3150d-108">例外狀況物件會存在直到結束擲出例外狀況的時間從`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="3150d-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="3150d-109">函式評估，這會由 ICorDebugEval 方法執行，將會清除例外狀況物件上設定，然後將其還原完成。</span><span class="sxs-lookup"><span data-stu-id="3150d-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="3150d-110">（例如，如果在篩選中，或在函式評估，則會擲回例外狀況），可以巢狀例外狀況，因此可能會有單一執行緒上的多個未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3150d-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="3150d-111">`GetCurrentException` 傳回最新的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3150d-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="3150d-112">例外狀況物件和型別可能會變更整個生命週期的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3150d-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="3150d-113">比方說，會擲回例外狀況型別 x 的之後，common language runtime (CLR) 可能會用盡記憶體，並將它升級到記憶體不足例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3150d-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3150d-114">需求</span><span class="sxs-lookup"><span data-stu-id="3150d-114">Requirements</span></span>  
 <span data-ttu-id="3150d-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3150d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3150d-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3150d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3150d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3150d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3150d-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3150d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
