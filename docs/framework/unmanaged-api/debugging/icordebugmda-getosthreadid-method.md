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
ms.openlocfilehash: 80248bba6d11b8af07aa0517cb41c8a4f783b5e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710892"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="7e47f-102">ICorDebugMDA::GetOSThreadId 方法</span><span class="sxs-lookup"><span data-stu-id="7e47f-102">ICorDebugMDA::GetOSThreadId Method</span></span>

<span data-ttu-id="7e47f-103">取得作業系統 (OS) 執行緒識別碼，在此識別碼上， [ICorDebugMDA](icordebugmda-interface.md) 所代表的 managed 偵錯工具 (MDA) 正在執行。</span><span class="sxs-lookup"><span data-stu-id="7e47f-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e47f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e47f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e47f-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e47f-105">Parameters</span></span>  

 `pOsTid`  
 <span data-ttu-id="7e47f-106">擴展OS 執行緒識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="7e47f-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e47f-107">備註</span><span class="sxs-lookup"><span data-stu-id="7e47f-107">Remarks</span></span>  

 <span data-ttu-id="7e47f-108">作業系統執行緒是用來取代 ICorDebugThread，以允許在原生執行緒或尚未進入 managed 程式碼的 managed 執行緒上引發 MDA 的情況。</span><span class="sxs-lookup"><span data-stu-id="7e47f-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e47f-109">需求</span><span class="sxs-lookup"><span data-stu-id="7e47f-109">Requirements</span></span>  

 <span data-ttu-id="7e47f-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e47f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e47f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e47f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e47f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e47f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e47f-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e47f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e47f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e47f-114">See also</span></span>

- [<span data-ttu-id="7e47f-115">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="7e47f-115">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="7e47f-116">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="7e47f-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
