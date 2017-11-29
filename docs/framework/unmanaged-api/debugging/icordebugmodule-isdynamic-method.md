---
title: "ICorDebugModule::IsDynamic 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsDynamic
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3583749ddb48015b43d45061d3e4cb10e08016b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="1f194-102">ICorDebugModule::IsDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="1f194-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="1f194-103">取得值，指出此模組是否為動態。</span><span class="sxs-lookup"><span data-stu-id="1f194-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f194-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f194-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f194-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f194-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="1f194-106">[out]`true`動態; 否則此模組是否`false`。</span><span class="sxs-lookup"><span data-stu-id="1f194-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f194-107">備註</span><span class="sxs-lookup"><span data-stu-id="1f194-107">Remarks</span></span>  
 <span data-ttu-id="1f194-108">動態模組可以新增新的類別，並刪除現有的類別，即使已載入的模組。</span><span class="sxs-lookup"><span data-stu-id="1f194-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="1f194-109">[Icordebugmanagedcallback:: Loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)和[icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼通知偵錯工具，當已加入或刪除類別。</span><span class="sxs-lookup"><span data-stu-id="1f194-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f194-110">需求</span><span class="sxs-lookup"><span data-stu-id="1f194-110">Requirements</span></span>  
 <span data-ttu-id="1f194-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f194-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f194-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f194-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f194-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f194-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f194-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f194-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
