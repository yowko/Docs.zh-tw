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
ms.openlocfilehash: 786582c7118fbed394de7c414a10243616cf4ee1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209795"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="865f0-102">ICorDebugManagedCallback::ExitAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="865f0-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="865f0-103">通知偵錯工具，應用程式域已結束。</span><span class="sxs-lookup"><span data-stu-id="865f0-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="865f0-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="865f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="865f0-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="865f0-106">在ICorDebugProcess 物件的指標，代表包含指定之應用程式域的進程。</span><span class="sxs-lookup"><span data-stu-id="865f0-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="865f0-107">在ICorDebugAppDomain 物件的指標，表示已結束的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="865f0-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865f0-108">需求</span><span class="sxs-lookup"><span data-stu-id="865f0-108">Requirements</span></span>  
 <span data-ttu-id="865f0-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="865f0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865f0-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="865f0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="865f0-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="865f0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="865f0-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865f0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865f0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="865f0-113">See also</span></span>

- [<span data-ttu-id="865f0-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="865f0-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
