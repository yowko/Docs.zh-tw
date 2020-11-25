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
ms.openlocfilehash: 1f6c6ae3b7cb45b049d0fb0d88bbf89121bccfd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710411"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="f847c-102">ICorDebugModule::EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="f847c-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>

<span data-ttu-id="f847c-103">控制是否針對此模組呼叫 [ICorDebugManagedCallback：： LoadClass](icordebugmanagedcallback-loadclass-method.md) 和 [ICorDebugManagedCallback：： UnloadClass](icordebugmanagedcallback-unloadclass-method.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="f847c-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f847c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f847c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f847c-105">參數</span><span class="sxs-lookup"><span data-stu-id="f847c-105">Parameters</span></span>  

 `bClassLoadCallbacks`  
 <span data-ttu-id="f847c-106">在將此值設為，可 `true` 讓 common language runtime (CLR) `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` 在相關聯的事件發生時呼叫和方法。</span><span class="sxs-lookup"><span data-stu-id="f847c-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="f847c-107">非動態模組的預設值為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f847c-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="f847c-108">動態模組的值一律 `true` 為，而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="f847c-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f847c-109">備註</span><span class="sxs-lookup"><span data-stu-id="f847c-109">Remarks</span></span>  

 <span data-ttu-id="f847c-110">`ICorDebugManagedCallback::LoadClass`和 `ICorDebugManagedCallback::UnloadClass` 回呼一律會啟用動態模組，而且無法停用。</span><span class="sxs-lookup"><span data-stu-id="f847c-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f847c-111">需求</span><span class="sxs-lookup"><span data-stu-id="f847c-111">Requirements</span></span>  

 <span data-ttu-id="f847c-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f847c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f847c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f847c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f847c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f847c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f847c-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f847c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f847c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f847c-116">See also</span></span>
