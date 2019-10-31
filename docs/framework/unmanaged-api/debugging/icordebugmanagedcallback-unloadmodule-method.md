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
ms.openlocfilehash: 70aaf32b9da751b49571ab98a95e432b7f84caa9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130642"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="a4b48-102">ICorDebugManagedCallback::UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="a4b48-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="a4b48-103">通知偵錯工具已卸載通用語言執行時間模組（DLL）。</span><span class="sxs-lookup"><span data-stu-id="a4b48-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b48-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4b48-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b48-105">參數</span><span class="sxs-lookup"><span data-stu-id="a4b48-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a4b48-106">在代表包含模組之應用程式域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="a4b48-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="a4b48-107">在代表模組之 ICorDebugModule 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a4b48-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4b48-108">備註</span><span class="sxs-lookup"><span data-stu-id="a4b48-108">Remarks</span></span>  
 <span data-ttu-id="a4b48-109">此呼叫之後，不應使用此模組。</span><span class="sxs-lookup"><span data-stu-id="a4b48-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b48-110">需求</span><span class="sxs-lookup"><span data-stu-id="a4b48-110">Requirements</span></span>  
 <span data-ttu-id="a4b48-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4b48-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b48-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4b48-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4b48-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4b48-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4b48-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b48-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a4b48-115">See also</span></span>

- [<span data-ttu-id="a4b48-116">LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="a4b48-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="a4b48-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a4b48-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
