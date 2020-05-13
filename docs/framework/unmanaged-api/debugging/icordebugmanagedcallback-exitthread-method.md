---
title: ICorDebugManagedCallback::ExitThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: 3ba1280aa44a9445f6af7fe9a8769b7cdc7edb66
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205252"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="257f4-102">ICorDebugManagedCallback::ExitThread 方法</span><span class="sxs-lookup"><span data-stu-id="257f4-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="257f4-103">通知偵錯工具，執行 managed 程式碼的執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="257f4-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="257f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="257f4-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="257f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="257f4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="257f4-106">在ICorDebugAppDomain 物件的指標，表示包含 managed 執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="257f4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="257f4-107">在代表 managed 執行緒之 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="257f4-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="257f4-108">備註</span><span class="sxs-lookup"><span data-stu-id="257f4-108">Remarks</span></span>  
 <span data-ttu-id="257f4-109">一旦 `ExitThread` 引發回呼，執行緒就不會再出現線上程列舉中。</span><span class="sxs-lookup"><span data-stu-id="257f4-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="257f4-110">需求</span><span class="sxs-lookup"><span data-stu-id="257f4-110">Requirements</span></span>  
 <span data-ttu-id="257f4-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="257f4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="257f4-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="257f4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="257f4-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="257f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="257f4-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="257f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="257f4-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="257f4-115">See also</span></span>

- [<span data-ttu-id="257f4-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="257f4-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
