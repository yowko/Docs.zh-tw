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
ms.openlocfilehash: 45b1d0c0a3199227ab644ba8732198dd14b1cb4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793001"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="d632e-102">ICorDebugModule::IsDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="d632e-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="d632e-103">取得值，指出此模組是否為動態。</span><span class="sxs-lookup"><span data-stu-id="d632e-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d632e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d632e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d632e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d632e-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="d632e-106">[out] `true` 如果這個模組是動態的，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="d632e-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d632e-107">備註</span><span class="sxs-lookup"><span data-stu-id="d632e-107">Remarks</span></span>  
 <span data-ttu-id="d632e-108">即使在載入模組之後，動態模組也可以加入新的類別，並刪除現有的類別。</span><span class="sxs-lookup"><span data-stu-id="d632e-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="d632e-109">[ICorDebugManagedCallback：： LoadClass](icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback：： UnloadClass](icordebugmanagedcallback-unloadclass-method.md)回呼會在新增或刪除類別時，通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d632e-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d632e-110">需求</span><span class="sxs-lookup"><span data-stu-id="d632e-110">Requirements</span></span>  
 <span data-ttu-id="d632e-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d632e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d632e-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d632e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d632e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d632e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d632e-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d632e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
