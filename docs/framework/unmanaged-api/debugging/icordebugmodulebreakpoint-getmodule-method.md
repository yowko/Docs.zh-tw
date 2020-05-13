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
ms.openlocfilehash: 714819504099ea978ed31d471b4ceb9fc17a6552
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212291"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="a112c-102">ICorDebugModuleBreakpoint::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="a112c-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="a112c-103">取得 "ICorDebugModule" 的介面指標，其參考此中斷點設定所在的模組。</span><span class="sxs-lookup"><span data-stu-id="a112c-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a112c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a112c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a112c-105">參數</span><span class="sxs-lookup"><span data-stu-id="a112c-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="a112c-106">脫銷介面位址的指標 `ICorDebugModule` ，參考已設定中斷點的模組。</span><span class="sxs-lookup"><span data-stu-id="a112c-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a112c-107">需求</span><span class="sxs-lookup"><span data-stu-id="a112c-107">Requirements</span></span>  
 <span data-ttu-id="a112c-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a112c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a112c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a112c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a112c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a112c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a112c-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a112c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a112c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a112c-112">See also</span></span>
