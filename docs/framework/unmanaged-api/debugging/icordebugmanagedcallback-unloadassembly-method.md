---
title: ICorDebugManagedCallback::UnloadAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 4ae4856eca2c1441ea53df0d9ed3648700b39b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130649"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="c4d55-102">ICorDebugManagedCallback::UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c4d55-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="c4d55-103">通知偵錯工具已卸載通用語言執行時間元件。</span><span class="sxs-lookup"><span data-stu-id="c4d55-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d55-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4d55-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4d55-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4d55-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c4d55-106">在ICorDebugAppDomain 物件的指標，表示包含該元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="c4d55-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="c4d55-107">在表示元件之 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="c4d55-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4d55-108">備註</span><span class="sxs-lookup"><span data-stu-id="c4d55-108">Remarks</span></span>  
 <span data-ttu-id="c4d55-109">此回呼之後，不應使用此元件。</span><span class="sxs-lookup"><span data-stu-id="c4d55-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d55-110">需求</span><span class="sxs-lookup"><span data-stu-id="c4d55-110">Requirements</span></span>  
 <span data-ttu-id="c4d55-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4d55-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d55-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4d55-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4d55-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4d55-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4d55-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d55-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d55-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4d55-115">See also</span></span>

- [<span data-ttu-id="c4d55-116">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c4d55-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="c4d55-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c4d55-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
