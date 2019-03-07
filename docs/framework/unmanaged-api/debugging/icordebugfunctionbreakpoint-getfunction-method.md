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
ms.openlocfilehash: a1da93ea073d6ae9f2e79f251014b2db5282a22c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496010"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="a2490-102">ICorDebugFunctionBreakpoint::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="a2490-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="a2490-103">取得參考函式設定中斷點 ICorDebugFunction 介面指標。</span><span class="sxs-lookup"><span data-stu-id="a2490-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2490-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2490-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2490-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2490-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="a2490-106">[out]設定中斷點的函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="a2490-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2490-107">需求</span><span class="sxs-lookup"><span data-stu-id="a2490-107">Requirements</span></span>  
 <span data-ttu-id="a2490-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2490-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2490-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2490-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2490-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2490-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2490-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2490-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
