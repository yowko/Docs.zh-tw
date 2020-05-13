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
ms.openlocfilehash: 4517f266bbb500223214a6a8fe5881e8b29566c3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206889"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="3eca8-102">ICorDebugModule::IsDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="3eca8-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="3eca8-103">取得值，指出此模組是否為動態。</span><span class="sxs-lookup"><span data-stu-id="3eca8-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eca8-104">語法</span><span class="sxs-lookup"><span data-stu-id="3eca8-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eca8-105">參數</span><span class="sxs-lookup"><span data-stu-id="3eca8-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="3eca8-106">[out] `true`如果此模組為動態，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="3eca8-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eca8-107">備註</span><span class="sxs-lookup"><span data-stu-id="3eca8-107">Remarks</span></span>  
 <span data-ttu-id="3eca8-108">即使在載入模組之後，動態模組也可以加入新的類別，並刪除現有的類別。</span><span class="sxs-lookup"><span data-stu-id="3eca8-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="3eca8-109">[ICorDebugManagedCallback：： LoadClass](icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback：： UnloadClass](icordebugmanagedcallback-unloadclass-method.md)回呼會在新增或刪除類別時，通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="3eca8-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eca8-110">需求</span><span class="sxs-lookup"><span data-stu-id="3eca8-110">Requirements</span></span>  
 <span data-ttu-id="3eca8-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3eca8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eca8-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3eca8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3eca8-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3eca8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eca8-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eca8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
