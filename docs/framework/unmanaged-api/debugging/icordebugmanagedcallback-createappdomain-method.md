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
ms.openlocfilehash: afd8bd76f8d738c9eaa3a8e3d490e175e408b92b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988282"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="8798a-102">ICorDebugManagedCallback::CreateAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="8798a-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="8798a-103">已建立的應用程式定義域會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8798a-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8798a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8798a-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8798a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8798a-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8798a-106">[in]ICorDebugProcess 物件，表示所建立的應用程式定義域中的程序的指標。</span><span class="sxs-lookup"><span data-stu-id="8798a-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="8798a-107">[in]表示已建立的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="8798a-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8798a-108">需求</span><span class="sxs-lookup"><span data-stu-id="8798a-108">Requirements</span></span>  
 <span data-ttu-id="8798a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8798a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8798a-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8798a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8798a-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8798a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8798a-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8798a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8798a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8798a-113">See also</span></span>

- [<span data-ttu-id="8798a-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8798a-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
