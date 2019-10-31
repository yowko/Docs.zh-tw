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
ms.openlocfilehash: 6f9d8cd79ac4107817d19fc0632aeaee287d253a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097006"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="fb51c-102">ICorDebugModuleBreakpoint::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="fb51c-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="fb51c-103">取得 "ICorDebugModule" 的介面指標，其參考此中斷點設定所在的模組。</span><span class="sxs-lookup"><span data-stu-id="fb51c-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb51c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb51c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb51c-105">參數</span><span class="sxs-lookup"><span data-stu-id="fb51c-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="fb51c-106">脫銷參考已設定中斷點之模組的 `ICorDebugModule` 介面位址的指標。</span><span class="sxs-lookup"><span data-stu-id="fb51c-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb51c-107">需求</span><span class="sxs-lookup"><span data-stu-id="fb51c-107">Requirements</span></span>  
 <span data-ttu-id="fb51c-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb51c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb51c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb51c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb51c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb51c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb51c-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb51c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb51c-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb51c-112">See also</span></span>
