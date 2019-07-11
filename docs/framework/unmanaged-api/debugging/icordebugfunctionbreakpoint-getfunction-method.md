---
title: ICorDebugFunctionBreakpoint::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4f9ea741e545cc424dff450325c3f8d271c8554
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755585"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="7ac6a-102">ICorDebugFunctionBreakpoint::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="7ac6a-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="7ac6a-103">取得參考函式設定中斷點 ICorDebugFunction 介面指標。</span><span class="sxs-lookup"><span data-stu-id="7ac6a-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ac6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ac6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ac6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ac6a-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="7ac6a-106">[out]設定中斷點的函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="7ac6a-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ac6a-107">需求</span><span class="sxs-lookup"><span data-stu-id="7ac6a-107">Requirements</span></span>  
 <span data-ttu-id="7ac6a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ac6a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ac6a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ac6a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ac6a-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ac6a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ac6a-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ac6a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
