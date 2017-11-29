---
title: "ICorDebugManagedCallback::LoadAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e59853f8f0ac61f89fc0efe0fb63f4ad7e6e0e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="88c16-102">ICorDebugManagedCallback::LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="88c16-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="88c16-103">已成功載入 common language runtime (CLR) 組件會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="88c16-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c16-104">語法</span><span class="sxs-lookup"><span data-stu-id="88c16-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88c16-105">參數</span><span class="sxs-lookup"><span data-stu-id="88c16-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="88c16-106">[in]代表應用程式定義域到其中的組件已載入 ICorDebugAppDomain 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="88c16-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="88c16-107">[in]代表組件 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="88c16-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88c16-108">需求</span><span class="sxs-lookup"><span data-stu-id="88c16-108">Requirements</span></span>  
 <span data-ttu-id="88c16-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88c16-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88c16-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88c16-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88c16-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88c16-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88c16-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88c16-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c16-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88c16-113">See Also</span></span>  
 [<span data-ttu-id="88c16-114">UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="88c16-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)  
 [<span data-ttu-id="88c16-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="88c16-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
