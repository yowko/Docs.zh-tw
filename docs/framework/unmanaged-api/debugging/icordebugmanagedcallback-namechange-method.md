---
title: ICorDebugManagedCallback::NameChange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 975353403a82956912fa41047253bb0dbf138502
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124120"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="35c28-102">ICorDebugManagedCallback::NameChange 方法</span><span class="sxs-lookup"><span data-stu-id="35c28-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="35c28-103">告知偵錯工具的應用程式定義域或執行緒名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="35c28-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c28-104">語法</span><span class="sxs-lookup"><span data-stu-id="35c28-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35c28-105">參數</span><span class="sxs-lookup"><span data-stu-id="35c28-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="35c28-106">[in]ICorDebugAppDomain 物件，表示必須變更名稱或應用程式定義域的指標會包含具有名稱變更的執行緒。</span><span class="sxs-lookup"><span data-stu-id="35c28-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="35c28-107">[in]ICorDebugThread 物件，表示有名稱變更的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="35c28-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35c28-108">需求</span><span class="sxs-lookup"><span data-stu-id="35c28-108">Requirements</span></span>  
 <span data-ttu-id="35c28-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35c28-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35c28-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35c28-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35c28-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35c28-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="35c28-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="35c28-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35c28-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35c28-113">See also</span></span>

- [<span data-ttu-id="35c28-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="35c28-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
