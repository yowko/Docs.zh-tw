---
title: "ICorDebugManagedCallback::CreateAppDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0f9b6322ee391edaba73e0c222b75aa86eee7e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="f7332-102">ICorDebugManagedCallback::CreateAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="f7332-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="f7332-103">告知偵錯工具已建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="f7332-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7332-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7332-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7332-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7332-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f7332-106">[in]表示所建立的應用程式定義域中的程序的 ICorDebugProcess 物件指標。</span><span class="sxs-lookup"><span data-stu-id="f7332-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f7332-107">[in]表示已建立的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="f7332-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7332-108">需求</span><span class="sxs-lookup"><span data-stu-id="f7332-108">Requirements</span></span>  
 <span data-ttu-id="f7332-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7332-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7332-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7332-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7332-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7332-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7332-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7332-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7332-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7332-113">See Also</span></span>  
 [<span data-ttu-id="f7332-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f7332-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
