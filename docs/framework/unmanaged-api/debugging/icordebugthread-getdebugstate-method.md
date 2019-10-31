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
ms.openlocfilehash: f054f8f2bd7c322e722a1e17290ba6fbad9e37b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133513"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="ea50e-102">ICorDebugThread::GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="ea50e-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="ea50e-103">取得這個 ICorDebugThread 物件的目前 debug 狀態。</span><span class="sxs-lookup"><span data-stu-id="ea50e-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea50e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea50e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea50e-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea50e-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="ea50e-106">脫銷CorDebugThreadState 列舉值的位元組合指標，描述這個執行緒目前的「偵錯工具」狀態。</span><span class="sxs-lookup"><span data-stu-id="ea50e-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea50e-107">備註</span><span class="sxs-lookup"><span data-stu-id="ea50e-107">Remarks</span></span>  
 <span data-ttu-id="ea50e-108">如果進程目前已停止，`pState` 代表此執行緒存在的 debug 狀態（如果進程要繼續），而不是此執行緒的實際目前狀態。</span><span class="sxs-lookup"><span data-stu-id="ea50e-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea50e-109">需求</span><span class="sxs-lookup"><span data-stu-id="ea50e-109">Requirements</span></span>  
 <span data-ttu-id="ea50e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea50e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea50e-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea50e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea50e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea50e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea50e-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea50e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
