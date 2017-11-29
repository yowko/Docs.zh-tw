---
title: "ICorDebugModule::EnableClassLoadCallbacks 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9045cceda54e6fe89c8c1baa8d4b9fa63105607
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="88a3b-102">ICorDebugModule::EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="88a3b-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="88a3b-103">控制項是否[icordebugmanagedcallback:: Loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)和[icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)針對此模組會呼叫的回呼。</span><span class="sxs-lookup"><span data-stu-id="88a3b-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a3b-104">語法</span><span class="sxs-lookup"><span data-stu-id="88a3b-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88a3b-105">參數</span><span class="sxs-lookup"><span data-stu-id="88a3b-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="88a3b-106">[in]將此值設定為`true`啟用 common language runtime (CLR) 呼叫`ICorDebugManagedCallback::LoadClass`和`ICorDebugManagedCallback::UnloadClass`方法與其相關聯的事件發生時。</span><span class="sxs-lookup"><span data-stu-id="88a3b-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="88a3b-107">預設值是`false`非動態模組。</span><span class="sxs-lookup"><span data-stu-id="88a3b-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="88a3b-108">這個值一律是`true`動態模組，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="88a3b-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88a3b-109">備註</span><span class="sxs-lookup"><span data-stu-id="88a3b-109">Remarks</span></span>  
 <span data-ttu-id="88a3b-110">`ICorDebugManagedCallback::LoadClass`和`ICorDebugManagedCallback::UnloadClass`回呼一定會啟用動態模組，且無法停用。</span><span class="sxs-lookup"><span data-stu-id="88a3b-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a3b-111">需求</span><span class="sxs-lookup"><span data-stu-id="88a3b-111">Requirements</span></span>  
 <span data-ttu-id="88a3b-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88a3b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88a3b-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88a3b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88a3b-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88a3b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88a3b-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88a3b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a3b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88a3b-116">See Also</span></span>  
    
 
