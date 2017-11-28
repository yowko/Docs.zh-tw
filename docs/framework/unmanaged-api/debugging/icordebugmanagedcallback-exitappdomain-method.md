---
title: "ICorDebugManagedCallback::ExitAppDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07f76d8add6c8b0e44eba241b7787b8e8a2de570
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="636ac-102">ICorDebugManagedCallback::ExitAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="636ac-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="636ac-103">告知偵錯工具應用程式定義域已結束。</span><span class="sxs-lookup"><span data-stu-id="636ac-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="636ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="636ac-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="636ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="636ac-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="636ac-106">[in]代表包含指定的應用程式網域的處理序 ICorDebugProcess 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="636ac-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="636ac-107">[in]表示已結束的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="636ac-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="636ac-108">需求</span><span class="sxs-lookup"><span data-stu-id="636ac-108">Requirements</span></span>  
 <span data-ttu-id="636ac-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="636ac-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="636ac-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="636ac-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="636ac-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="636ac-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="636ac-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="636ac-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="636ac-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="636ac-113">See Also</span></span>  
 [<span data-ttu-id="636ac-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="636ac-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
