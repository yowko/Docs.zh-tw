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
ms.openlocfilehash: fa649fd1983a76c71d400ad3e6965ac0794da6ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781601"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="44d2c-102">ICorDebugManagedCallback::ExitThread 方法</span><span class="sxs-lookup"><span data-stu-id="44d2c-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="44d2c-103">通知偵錯工具，執行 managed 程式碼的執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="44d2c-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="44d2c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44d2c-105">參數</span><span class="sxs-lookup"><span data-stu-id="44d2c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="44d2c-106">在ICorDebugAppDomain 物件的指標，表示包含 managed 執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="44d2c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="44d2c-107">在代表 managed 執行緒之 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="44d2c-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44d2c-108">備註</span><span class="sxs-lookup"><span data-stu-id="44d2c-108">Remarks</span></span>  
 <span data-ttu-id="44d2c-109">一旦引發 `ExitThread` 回呼，執行緒就不會再出現線上程列舉中。</span><span class="sxs-lookup"><span data-stu-id="44d2c-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44d2c-110">需求</span><span class="sxs-lookup"><span data-stu-id="44d2c-110">Requirements</span></span>  
 <span data-ttu-id="44d2c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44d2c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d2c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44d2c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44d2c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44d2c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44d2c-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d2c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="44d2c-115">See also</span></span>

- [<span data-ttu-id="44d2c-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="44d2c-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
