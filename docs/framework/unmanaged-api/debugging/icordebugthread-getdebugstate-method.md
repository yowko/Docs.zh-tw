---
title: ICorDebugThread::GetDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 746fef3629e6573d7dfe47d5a3fcf9ee9a1d4250
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728039"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="69a21-102">ICorDebugThread::GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="69a21-102">ICorDebugThread::GetDebugState Method</span></span>

<span data-ttu-id="69a21-103">取得這個 ICorDebugThread 物件的目前偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="69a21-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a21-104">語法</span><span class="sxs-lookup"><span data-stu-id="69a21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69a21-105">參數</span><span class="sxs-lookup"><span data-stu-id="69a21-105">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="69a21-106">擴展CorDebugThreadState 列舉值的位元組合指標，這些值會描述這個執行緒目前的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="69a21-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69a21-107">備註</span><span class="sxs-lookup"><span data-stu-id="69a21-107">Remarks</span></span>  

 <span data-ttu-id="69a21-108">如果進程目前已停止， `pState` 表示此執行緒的偵測狀態（如果進程已繼續，而非此執行緒的實際目前狀態）。</span><span class="sxs-lookup"><span data-stu-id="69a21-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69a21-109">需求</span><span class="sxs-lookup"><span data-stu-id="69a21-109">Requirements</span></span>  

 <span data-ttu-id="69a21-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69a21-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69a21-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69a21-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69a21-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69a21-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69a21-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69a21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
