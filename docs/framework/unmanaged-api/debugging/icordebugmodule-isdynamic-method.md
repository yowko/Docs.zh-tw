---
title: ICorDebugModule::IsDynamic 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db5d07d2b9a295a5cd21b4d4af954503b8bd7a8b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763665"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="8b4f0-102">ICorDebugModule::IsDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="8b4f0-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="8b4f0-103">取得值，指出此模組是否為動態。</span><span class="sxs-lookup"><span data-stu-id="8b4f0-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b4f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b4f0-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b4f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b4f0-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="8b4f0-106">[out]`true`如果此模組是動態的否則`false`。</span><span class="sxs-lookup"><span data-stu-id="8b4f0-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b4f0-107">備註</span><span class="sxs-lookup"><span data-stu-id="8b4f0-107">Remarks</span></span>  
 <span data-ttu-id="8b4f0-108">動態模組可以新增新的類別，並刪除現有的類別，即使已載入模組。</span><span class="sxs-lookup"><span data-stu-id="8b4f0-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="8b4f0-109">[Icordebugmanagedcallback:: Loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)並[icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼通知偵錯工具，當已加入或刪除類別。</span><span class="sxs-lookup"><span data-stu-id="8b4f0-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b4f0-110">需求</span><span class="sxs-lookup"><span data-stu-id="8b4f0-110">Requirements</span></span>  
 <span data-ttu-id="8b4f0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b4f0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b4f0-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b4f0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b4f0-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b4f0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b4f0-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b4f0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
