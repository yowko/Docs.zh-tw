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
ms.openlocfilehash: 1ca3adf30ad633fcfb10a4b43a435698d2899597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213526"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="b6b32-102">ICorDebugModule::EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="b6b32-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="b6b32-103">控制是否針對此模組呼叫[ICorDebugManagedCallback：： LoadClass](icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback：： UnloadClass](icordebugmanagedcallback-unloadclass-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="b6b32-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b32-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6b32-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6b32-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6b32-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="b6b32-106">在將此值設定為， `true` 可讓 common language runtime （CLR） `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` 在相關聯的事件發生時呼叫和方法。</span><span class="sxs-lookup"><span data-stu-id="b6b32-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="b6b32-107">非動態模組的預設值為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="b6b32-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="b6b32-108">動態模組的值一律 `true` 為，而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="b6b32-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6b32-109">備註</span><span class="sxs-lookup"><span data-stu-id="b6b32-109">Remarks</span></span>  
 <span data-ttu-id="b6b32-110">`ICorDebugManagedCallback::LoadClass`和 `ICorDebugManagedCallback::UnloadClass` 回呼一律會針對動態模組啟用，且無法停用。</span><span class="sxs-lookup"><span data-stu-id="b6b32-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b32-111">需求</span><span class="sxs-lookup"><span data-stu-id="b6b32-111">Requirements</span></span>  
 <span data-ttu-id="b6b32-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b32-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b32-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6b32-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6b32-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6b32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6b32-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6b32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b32-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b32-116">See also</span></span>
