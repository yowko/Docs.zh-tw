---
title: ICorDebugModule::GetAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce1e42d74dc611032d941e833bb8f248a56488b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486248"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="98ae5-102">ICorDebugModule::GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="98ae5-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="98ae5-103">取得此模組包含組件。</span><span class="sxs-lookup"><span data-stu-id="98ae5-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ae5-104">語法</span><span class="sxs-lookup"><span data-stu-id="98ae5-104">Syntax</span></span>  
  
```  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98ae5-105">參數</span><span class="sxs-lookup"><span data-stu-id="98ae5-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="98ae5-106">[out]ICorDebugAssembly 物件，表示包含此模組的組件的指標。</span><span class="sxs-lookup"><span data-stu-id="98ae5-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98ae5-107">需求</span><span class="sxs-lookup"><span data-stu-id="98ae5-107">Requirements</span></span>  
 <span data-ttu-id="98ae5-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98ae5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98ae5-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98ae5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98ae5-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98ae5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98ae5-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98ae5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
