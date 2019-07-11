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
ms.openlocfilehash: ec9b4867ad19f25e35ca31c007c0d238b949abab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762219"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="97bd6-102">ICorDebugModule::EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="97bd6-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="97bd6-103">控制項是否[icordebugmanagedcallback:: Loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)並[icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼會呼叫此模組。</span><span class="sxs-lookup"><span data-stu-id="97bd6-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97bd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="97bd6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97bd6-105">參數</span><span class="sxs-lookup"><span data-stu-id="97bd6-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="97bd6-106">[in]將此值設定為`true`若要啟用 common language runtime (CLR) 呼叫`ICorDebugManagedCallback::LoadClass`和`ICorDebugManagedCallback::UnloadClass`及其相關聯的事件發生時的方法。</span><span class="sxs-lookup"><span data-stu-id="97bd6-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="97bd6-107">預設值是`false`非動態模組。</span><span class="sxs-lookup"><span data-stu-id="97bd6-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="97bd6-108">這個值一律是`true`動態模組，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="97bd6-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97bd6-109">備註</span><span class="sxs-lookup"><span data-stu-id="97bd6-109">Remarks</span></span>  
 <span data-ttu-id="97bd6-110">`ICorDebugManagedCallback::LoadClass`和`ICorDebugManagedCallback::UnloadClass`回呼一定會啟用動態模組，且無法停用。</span><span class="sxs-lookup"><span data-stu-id="97bd6-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97bd6-111">需求</span><span class="sxs-lookup"><span data-stu-id="97bd6-111">Requirements</span></span>  
 <span data-ttu-id="97bd6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97bd6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97bd6-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97bd6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97bd6-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97bd6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97bd6-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97bd6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97bd6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97bd6-116">See also</span></span>
