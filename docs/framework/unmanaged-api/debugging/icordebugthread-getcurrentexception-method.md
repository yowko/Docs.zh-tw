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
ms.openlocfilehash: 8082b2a3654f1605f18f3b68f54464dc83c8e60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133482"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="c0bbb-102">ICorDebugThread::GetCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="c0bbb-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="c0bbb-103">取得 ICorDebugValue 物件的介面指標，代表目前由 managed 程式碼擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0bbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0bbb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0bbb-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0bbb-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="c0bbb-106">脫銷`ICorDebugValue` 物件之位址的指標，代表目前由 managed 程式碼擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0bbb-107">備註</span><span class="sxs-lookup"><span data-stu-id="c0bbb-107">Remarks</span></span>  
 <span data-ttu-id="c0bbb-108">例外狀況物件會從擲回例外狀況的時間開始，直到 `catch` 區塊結束為止。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="c0bbb-109">函式評估是由 ICorDebugEval 方法執行，會在安裝時清除例外狀況物件，並在完成時將它還原。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="c0bbb-110">例外狀況可以是嵌套的（例如，如果在篩選準則中擲回例外狀況或在函式評估中擲回），因此單一線程上可能會有多個未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="c0bbb-111">`GetCurrentException` 會傳回最新的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="c0bbb-112">例外狀況物件和類型在例外狀況的整個生命週期中可能會變更。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="c0bbb-113">例如，擲回 x 類型的例外狀況之後，common language runtime （CLR）可能會耗盡記憶體，並將它升級為記憶體不足的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0bbb-114">需求</span><span class="sxs-lookup"><span data-stu-id="c0bbb-114">Requirements</span></span>  
 <span data-ttu-id="c0bbb-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0bbb-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0bbb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0bbb-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0bbb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0bbb-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0bbb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
