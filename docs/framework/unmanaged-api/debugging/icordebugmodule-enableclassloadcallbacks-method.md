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
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139225"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="63448-102">ICorDebugModule::EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="63448-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="63448-103">控制是否針對此模組呼叫[ICorDebugManagedCallback：： LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback：： UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="63448-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63448-104">語法</span><span class="sxs-lookup"><span data-stu-id="63448-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63448-105">參數</span><span class="sxs-lookup"><span data-stu-id="63448-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="63448-106">在將此值設定為 `true`，讓 common language runtime （CLR）在其相關聯的事件發生時，呼叫 `ICorDebugManagedCallback::LoadClass` 和 `ICorDebugManagedCallback::UnloadClass` 方法。</span><span class="sxs-lookup"><span data-stu-id="63448-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="63448-107">非動態模組的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="63448-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="63448-108">動態模組的值一律為 `true`，而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="63448-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63448-109">備註</span><span class="sxs-lookup"><span data-stu-id="63448-109">Remarks</span></span>  
 <span data-ttu-id="63448-110">動態模組的 `ICorDebugManagedCallback::LoadClass` 和 `ICorDebugManagedCallback::UnloadClass` 回呼一律會啟用，且無法停用。</span><span class="sxs-lookup"><span data-stu-id="63448-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63448-111">需求</span><span class="sxs-lookup"><span data-stu-id="63448-111">Requirements</span></span>  
 <span data-ttu-id="63448-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63448-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63448-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63448-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63448-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63448-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63448-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63448-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63448-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="63448-116">See also</span></span>
