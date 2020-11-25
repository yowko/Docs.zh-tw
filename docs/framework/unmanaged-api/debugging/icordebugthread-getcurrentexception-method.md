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
ms.openlocfilehash: c21be7b062b7e2d4129bafabae004351442ab853
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728052"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="825d4-102">ICorDebugThread::GetCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="825d4-102">ICorDebugThread::GetCurrentException Method</span></span>

<span data-ttu-id="825d4-103">取得 ICorDebugValue 物件的介面指標，該物件代表 managed 程式碼目前正在擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="825d4-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="825d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="825d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="825d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="825d4-105">Parameters</span></span>  

 `ppExceptionObject`  
 <span data-ttu-id="825d4-106">擴展物件位址的指標 `ICorDebugValue` ，該物件代表 managed 程式碼目前擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="825d4-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="825d4-107">備註</span><span class="sxs-lookup"><span data-stu-id="825d4-107">Remarks</span></span>  

 <span data-ttu-id="825d4-108">例外狀況物件將存在於擲回例外狀況的時間，直到區塊結束為止 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="825d4-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="825d4-109">函數評估（由 ICorDebugEval 方法執行）將會清除安裝程式上的例外狀況物件，並在完成時將其還原。</span><span class="sxs-lookup"><span data-stu-id="825d4-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="825d4-110">例外狀況可以是嵌套 (例如，如果在篩選中擲回例外狀況，或在函式評估) 中擲回例外狀況，因此單一線程上可能會有多個未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="825d4-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="825d4-111">`GetCurrentException` 傳回最新的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="825d4-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="825d4-112">例外狀況物件和類型可能會在例外狀況的整個存留期間變更。</span><span class="sxs-lookup"><span data-stu-id="825d4-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="825d4-113">例如，在擲回 x 類型的例外狀況之後，common language runtime (CLR) 可能會用盡記憶體，並將其升級為記憶體不足的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="825d4-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="825d4-114">需求</span><span class="sxs-lookup"><span data-stu-id="825d4-114">Requirements</span></span>  

 <span data-ttu-id="825d4-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="825d4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="825d4-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="825d4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="825d4-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="825d4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="825d4-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="825d4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
