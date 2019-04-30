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
ms.openlocfilehash: 51403c52d7f8a216e83b817f157979f4af1c433a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994769"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="97692-102">ICorDebugModuleBreakpoint::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="97692-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="97692-103">取得"ICorDebugModule 」 參考此中斷點被設定模組的介面指標。</span><span class="sxs-lookup"><span data-stu-id="97692-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97692-104">語法</span><span class="sxs-lookup"><span data-stu-id="97692-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97692-105">參數</span><span class="sxs-lookup"><span data-stu-id="97692-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="97692-106">[out]位址指標`ICorDebugModule`參考的模組設定中斷點的介面。</span><span class="sxs-lookup"><span data-stu-id="97692-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97692-107">需求</span><span class="sxs-lookup"><span data-stu-id="97692-107">Requirements</span></span>  
 <span data-ttu-id="97692-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97692-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97692-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97692-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97692-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97692-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97692-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97692-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97692-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97692-112">See also</span></span>
