---
title: ICorDebugManagedCallback::CreateAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3958e62f23615d4c9038713bb973a6d16424f348
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759721"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="e8abe-102">ICorDebugManagedCallback::CreateAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="e8abe-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="e8abe-103">已建立的應用程式定義域會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e8abe-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8abe-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8abe-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8abe-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8abe-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e8abe-106">[in]ICorDebugProcess 物件，表示所建立的應用程式定義域中的程序的指標。</span><span class="sxs-lookup"><span data-stu-id="e8abe-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="e8abe-107">[in]表示已建立的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="e8abe-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8abe-108">需求</span><span class="sxs-lookup"><span data-stu-id="e8abe-108">Requirements</span></span>  
 <span data-ttu-id="e8abe-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8abe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8abe-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8abe-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8abe-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8abe-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8abe-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8abe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8abe-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8abe-113">See also</span></span>

- [<span data-ttu-id="e8abe-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e8abe-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
