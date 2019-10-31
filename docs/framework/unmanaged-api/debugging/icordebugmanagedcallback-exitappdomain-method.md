---
title: ICorDebugManagedCallback::ExitAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: 5ba6ce4e59057442a9f17338ec7bfff787bd5d05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130799"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="cc57a-102">ICorDebugManagedCallback::ExitAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="cc57a-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="cc57a-103">通知偵錯工具，應用程式域已結束。</span><span class="sxs-lookup"><span data-stu-id="cc57a-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc57a-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc57a-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc57a-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc57a-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="cc57a-106">在ICorDebugProcess 物件的指標，代表包含指定之應用程式域的進程。</span><span class="sxs-lookup"><span data-stu-id="cc57a-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="cc57a-107">在ICorDebugAppDomain 物件的指標，表示已結束的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="cc57a-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc57a-108">需求</span><span class="sxs-lookup"><span data-stu-id="cc57a-108">Requirements</span></span>  
 <span data-ttu-id="cc57a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc57a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc57a-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc57a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc57a-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc57a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc57a-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc57a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc57a-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc57a-113">See also</span></span>

- [<span data-ttu-id="cc57a-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cc57a-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
