---
title: ICorDebugMDA::GetOSThreadId 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51d29fed3d53611daa0042251ce09638399f7ed5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723143"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="e44d7-102">ICorDebugMDA::GetOSThreadId 方法</span><span class="sxs-lookup"><span data-stu-id="e44d7-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="e44d7-103">取得所表示的 managed 偵錯助理 (MDA) 的作業系統 (OS) 執行緒識別碼[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)正在執行。</span><span class="sxs-lookup"><span data-stu-id="e44d7-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e44d7-104">Syntax</span></span>  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e44d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e44d7-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="e44d7-106">[out]OS 執行緒識別項指標。</span><span class="sxs-lookup"><span data-stu-id="e44d7-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e44d7-107">備註</span><span class="sxs-lookup"><span data-stu-id="e44d7-107">Remarks</span></span>  
 <span data-ttu-id="e44d7-108">OS 執行緒代替 ICorDebugThread 中，以允許在原生執行緒或尚未輸入 managed 程式碼，managed 執行緒上，會引發 MDA 的情況。</span><span class="sxs-lookup"><span data-stu-id="e44d7-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e44d7-109">需求</span><span class="sxs-lookup"><span data-stu-id="e44d7-109">Requirements</span></span>  
 <span data-ttu-id="e44d7-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e44d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e44d7-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e44d7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e44d7-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e44d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e44d7-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e44d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44d7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e44d7-114">See also</span></span>

- [<span data-ttu-id="e44d7-115">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="e44d7-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="e44d7-116">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="e44d7-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
