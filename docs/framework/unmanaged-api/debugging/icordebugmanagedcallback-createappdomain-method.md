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
ms.openlocfilehash: 6d2cb90f780d4d680e6c81ebd9579341d5a3b1fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="98b61-102">ICorDebugManagedCallback::CreateAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="98b61-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="98b61-103">告知偵錯工具已建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="98b61-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98b61-104">語法</span><span class="sxs-lookup"><span data-stu-id="98b61-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98b61-105">參數</span><span class="sxs-lookup"><span data-stu-id="98b61-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="98b61-106">[in]表示所建立的應用程式定義域中的程序的 ICorDebugProcess 物件指標。</span><span class="sxs-lookup"><span data-stu-id="98b61-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="98b61-107">[in]表示已建立的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="98b61-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98b61-108">需求</span><span class="sxs-lookup"><span data-stu-id="98b61-108">Requirements</span></span>  
 <span data-ttu-id="98b61-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98b61-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98b61-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98b61-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98b61-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98b61-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98b61-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98b61-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b61-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98b61-113">See Also</span></span>  
 [<span data-ttu-id="98b61-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="98b61-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
