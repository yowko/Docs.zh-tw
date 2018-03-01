---
title: "ICorDebugManagedCallback::LoadModule 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d17001db68043f5d46a90738a8ad3e0635de762
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="709e5-102">ICorDebugManagedCallback::LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="709e5-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="709e5-103">已成功載入的 common language runtime (CLR) 模組會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="709e5-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="709e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="709e5-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="709e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="709e5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="709e5-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域到其中已載入的模組指標。</span><span class="sxs-lookup"><span data-stu-id="709e5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="709e5-107">[in]表示 CLR 模組 ICorDebugModule 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="709e5-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="709e5-108">備註</span><span class="sxs-lookup"><span data-stu-id="709e5-108">Remarks</span></span>  
 <span data-ttu-id="709e5-109">`LoadModule`回呼會提供適當的時間檢查模組的中繼資料、 設定在 just-in-time (JIT) 編譯器旗標，或啟用或停用類別載入模組的回呼。</span><span class="sxs-lookup"><span data-stu-id="709e5-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="709e5-110">需求</span><span class="sxs-lookup"><span data-stu-id="709e5-110">Requirements</span></span>  
 <span data-ttu-id="709e5-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="709e5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="709e5-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="709e5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="709e5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="709e5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="709e5-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="709e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709e5-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="709e5-115">See Also</span></span>  
 [<span data-ttu-id="709e5-116">UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="709e5-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [<span data-ttu-id="709e5-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="709e5-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
