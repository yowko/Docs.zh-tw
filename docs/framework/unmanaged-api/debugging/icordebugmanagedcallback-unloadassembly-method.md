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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e770602858761dbcf15c233dceebfd35be106aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995094"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="a750f-102">ICorDebugManagedCallback::UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="a750f-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="a750f-103">Common language runtime 組件已卸載會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a750f-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a750f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a750f-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a750f-105">參數</span><span class="sxs-lookup"><span data-stu-id="a750f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a750f-106">[in]表示包含組件的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="a750f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="a750f-107">[in]代表組件 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a750f-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a750f-108">備註</span><span class="sxs-lookup"><span data-stu-id="a750f-108">Remarks</span></span>  
 <span data-ttu-id="a750f-109">在此回呼之後應不到組件。</span><span class="sxs-lookup"><span data-stu-id="a750f-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a750f-110">需求</span><span class="sxs-lookup"><span data-stu-id="a750f-110">Requirements</span></span>  
 <span data-ttu-id="a750f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a750f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a750f-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a750f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a750f-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a750f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a750f-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a750f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a750f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a750f-115">See also</span></span>

- [<span data-ttu-id="a750f-116">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="a750f-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="a750f-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a750f-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
