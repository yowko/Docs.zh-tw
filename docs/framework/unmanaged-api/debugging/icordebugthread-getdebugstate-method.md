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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0baabbb736365b138d1754e68070207b4310bf57
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762455"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="06bd7-102">ICorDebugThread::GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="06bd7-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="06bd7-103">取得這個 ICorDebugThread 物件的目前偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="06bd7-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06bd7-104">語法</span><span class="sxs-lookup"><span data-stu-id="06bd7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06bd7-105">參數</span><span class="sxs-lookup"><span data-stu-id="06bd7-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="06bd7-106">[out]位元組合 CorDebugThreadState 列舉值，描述這個執行緒的目前偵錯狀態指標。</span><span class="sxs-lookup"><span data-stu-id="06bd7-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06bd7-107">備註</span><span class="sxs-lookup"><span data-stu-id="06bd7-107">Remarks</span></span>  
 <span data-ttu-id="06bd7-108">如果目前已停止處理程序，`pState`代表只存在於這個執行緒繼續執行，不實際目前執行緒的狀態這程序時的偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="06bd7-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06bd7-109">需求</span><span class="sxs-lookup"><span data-stu-id="06bd7-109">Requirements</span></span>  
 <span data-ttu-id="06bd7-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06bd7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06bd7-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06bd7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06bd7-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06bd7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06bd7-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06bd7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
