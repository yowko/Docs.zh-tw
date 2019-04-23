---
title: ICorDebugModule::EnableClassLoadCallbacks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22a838748414f9d89cdc7ff469f7f5cc5e11b9d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108299"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="8be1d-102">ICorDebugModule::EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="8be1d-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="8be1d-103">控制項是否[icordebugmanagedcallback:: Loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)並[icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼會呼叫此模組。</span><span class="sxs-lookup"><span data-stu-id="8be1d-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="8be1d-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be1d-105">參數</span><span class="sxs-lookup"><span data-stu-id="8be1d-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="8be1d-106">[in]將此值設定為`true`若要啟用 common language runtime (CLR) 呼叫`ICorDebugManagedCallback::LoadClass`和`ICorDebugManagedCallback::UnloadClass`及其相關聯的事件發生時的方法。</span><span class="sxs-lookup"><span data-stu-id="8be1d-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="8be1d-107">預設值是`false`非動態模組。</span><span class="sxs-lookup"><span data-stu-id="8be1d-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="8be1d-108">這個值一律是`true`動態模組，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="8be1d-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8be1d-109">備註</span><span class="sxs-lookup"><span data-stu-id="8be1d-109">Remarks</span></span>  
 <span data-ttu-id="8be1d-110">`ICorDebugManagedCallback::LoadClass`和`ICorDebugManagedCallback::UnloadClass`回呼一定會啟用動態模組，且無法停用。</span><span class="sxs-lookup"><span data-stu-id="8be1d-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be1d-111">需求</span><span class="sxs-lookup"><span data-stu-id="8be1d-111">Requirements</span></span>  
 <span data-ttu-id="8be1d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8be1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be1d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8be1d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8be1d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8be1d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8be1d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be1d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8be1d-116">See also</span></span>
