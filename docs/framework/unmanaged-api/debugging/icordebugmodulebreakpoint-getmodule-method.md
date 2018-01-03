---
title: "ICorDebugModuleBreakpoint::GetModule 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint.GetModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91e014a16420ea6790b592efe1ac57df960d2237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="3e208-102">ICorDebugModuleBreakpoint::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="3e208-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="3e208-103">取得 「 ICorDebugModule"參考此中斷點被設定的模組的介面指標。</span><span class="sxs-lookup"><span data-stu-id="3e208-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e208-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e208-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e208-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e208-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="3e208-106">[out]位址指標`ICorDebugModule`參考的模組中設定中斷點的介面。</span><span class="sxs-lookup"><span data-stu-id="3e208-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e208-107">需求</span><span class="sxs-lookup"><span data-stu-id="3e208-107">Requirements</span></span>  
 <span data-ttu-id="3e208-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e208-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e208-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e208-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e208-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e208-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e208-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e208-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e208-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e208-112">See Also</span></span>  
 
