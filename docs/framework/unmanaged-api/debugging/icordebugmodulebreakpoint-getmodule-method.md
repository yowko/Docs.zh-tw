---
title: ICorDebugModuleBreakpoint::GetModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d4c0488adb38360d096c5827d078b0fbecc635
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498974"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="e1c4d-102">ICorDebugModuleBreakpoint::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="e1c4d-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="e1c4d-103">取得"ICorDebugModule 」 參考此中斷點被設定模組的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e1c4d-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1c4d-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1c4d-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="e1c4d-106">[out]位址指標`ICorDebugModule`參考的模組設定中斷點的介面。</span><span class="sxs-lookup"><span data-stu-id="e1c4d-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c4d-107">需求</span><span class="sxs-lookup"><span data-stu-id="e1c4d-107">Requirements</span></span>  
 <span data-ttu-id="e1c4d-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c4d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c4d-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1c4d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1c4d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1c4d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1c4d-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c4d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c4d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1c4d-112">See also</span></span>

