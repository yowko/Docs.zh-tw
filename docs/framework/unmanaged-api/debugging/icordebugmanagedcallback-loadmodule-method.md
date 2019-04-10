---
title: ICorDebugManagedCallback::LoadModule 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfca06c656f3274f4c5ddb06373a0296dc5e6905
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164537"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="67087-102">ICorDebugManagedCallback::LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="67087-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="67087-103">已成功載入的 common language runtime (CLR) 模組會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="67087-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67087-104">語法</span><span class="sxs-lookup"><span data-stu-id="67087-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67087-105">參數</span><span class="sxs-lookup"><span data-stu-id="67087-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="67087-106">[in]表示模組已經載入的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="67087-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="67087-107">[in]ICorDebugModule 物件，表示 CLR 模組指標。</span><span class="sxs-lookup"><span data-stu-id="67087-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67087-108">備註</span><span class="sxs-lookup"><span data-stu-id="67087-108">Remarks</span></span>  
 <span data-ttu-id="67087-109">`LoadModule`回呼提供適當的時間，檢查模組的中繼資料、 設定在 just-in-time (JIT) 編譯器旗標，或啟用或停用類別的載入模組的回呼。</span><span class="sxs-lookup"><span data-stu-id="67087-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67087-110">需求</span><span class="sxs-lookup"><span data-stu-id="67087-110">Requirements</span></span>  
 <span data-ttu-id="67087-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67087-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67087-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67087-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67087-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67087-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="67087-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="67087-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67087-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67087-115">See also</span></span>

- [<span data-ttu-id="67087-116">UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="67087-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="67087-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="67087-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
