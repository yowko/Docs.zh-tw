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
ms.openlocfilehash: 7bfa71ccff4a65e72a6b548a09d27648b67c0ae5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781846"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="8a831-102">ICorDebugManagedCallback::ExitAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="8a831-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="8a831-103">通知偵錯工具，應用程式域已結束。</span><span class="sxs-lookup"><span data-stu-id="8a831-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a831-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a831-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a831-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a831-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8a831-106">在ICorDebugProcess 物件的指標，代表包含指定之應用程式域的進程。</span><span class="sxs-lookup"><span data-stu-id="8a831-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="8a831-107">在ICorDebugAppDomain 物件的指標，表示已結束的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="8a831-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a831-108">需求</span><span class="sxs-lookup"><span data-stu-id="8a831-108">Requirements</span></span>  
 <span data-ttu-id="8a831-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a831-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a831-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a831-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a831-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a831-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a831-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a831-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a831-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a831-113">See also</span></span>

- [<span data-ttu-id="8a831-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8a831-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
