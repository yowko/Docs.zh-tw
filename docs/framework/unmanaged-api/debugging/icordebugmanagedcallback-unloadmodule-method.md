---
title: ICorDebugManagedCallback::UnloadModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae4c1cb251f7786a8415449f16b4eb26d15a4fb2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491265"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="846fa-102">ICorDebugManagedCallback::UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="846fa-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="846fa-103">告知偵錯工具通用語言執行階段模組 (DLL)，已卸載。</span><span class="sxs-lookup"><span data-stu-id="846fa-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="846fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="846fa-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="846fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="846fa-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="846fa-106">[in]表示包含模組的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="846fa-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="846fa-107">[in]ICorDebugModule 物件，表示模組指標。</span><span class="sxs-lookup"><span data-stu-id="846fa-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="846fa-108">備註</span><span class="sxs-lookup"><span data-stu-id="846fa-108">Remarks</span></span>  
 <span data-ttu-id="846fa-109">模組不應該使用這個呼叫之後。</span><span class="sxs-lookup"><span data-stu-id="846fa-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="846fa-110">需求</span><span class="sxs-lookup"><span data-stu-id="846fa-110">Requirements</span></span>  
 <span data-ttu-id="846fa-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="846fa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="846fa-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="846fa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="846fa-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="846fa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="846fa-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846fa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846fa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="846fa-115">See also</span></span>
- [<span data-ttu-id="846fa-116">LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="846fa-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="846fa-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="846fa-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
