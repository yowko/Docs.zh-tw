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
ms.openlocfilehash: 13125f60f596cb8a80d9c42c51a979f632de494b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379749"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="37481-102">ICorDebugThread::GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="37481-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="37481-103">取得這個 ICorDebugThread 物件的目前 debug 狀態。</span><span class="sxs-lookup"><span data-stu-id="37481-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37481-104">語法</span><span class="sxs-lookup"><span data-stu-id="37481-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37481-105">參數</span><span class="sxs-lookup"><span data-stu-id="37481-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="37481-106">脫銷CorDebugThreadState 列舉值的位元組合指標，描述這個執行緒目前的「偵錯工具」狀態。</span><span class="sxs-lookup"><span data-stu-id="37481-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37481-107">備註</span><span class="sxs-lookup"><span data-stu-id="37481-107">Remarks</span></span>  
 <span data-ttu-id="37481-108">如果進程目前已停止， `pState` 表示如果進程要繼續，而不是此執行緒的實際目前狀態時，這個執行緒會存在的 debug 狀態。</span><span class="sxs-lookup"><span data-stu-id="37481-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37481-109">需求</span><span class="sxs-lookup"><span data-stu-id="37481-109">Requirements</span></span>  
 <span data-ttu-id="37481-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37481-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37481-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37481-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37481-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37481-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37481-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37481-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
