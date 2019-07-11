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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e045c475b57f863071eb81194868b7db3c5a3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755804"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="1dab9-102">ICorDebugManagedCallback::ExitAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1dab9-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="1dab9-103">已結束應用程式定義域會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1dab9-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dab9-104">語法</span><span class="sxs-lookup"><span data-stu-id="1dab9-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dab9-105">參數</span><span class="sxs-lookup"><span data-stu-id="1dab9-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="1dab9-106">[in]ICorDebugProcess 物件，表示包含指定的應用程式定義域的處理序的指標。</span><span class="sxs-lookup"><span data-stu-id="1dab9-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1dab9-107">[in]表示已結束的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="1dab9-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dab9-108">需求</span><span class="sxs-lookup"><span data-stu-id="1dab9-108">Requirements</span></span>  
 <span data-ttu-id="1dab9-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dab9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dab9-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1dab9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dab9-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dab9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dab9-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dab9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dab9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dab9-113">See also</span></span>

- [<span data-ttu-id="1dab9-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1dab9-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
