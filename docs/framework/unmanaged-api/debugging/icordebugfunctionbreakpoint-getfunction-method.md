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
ms.openlocfilehash: 79a6c70399d5059d6959ac6127f22807138c00fa
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213110"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="a616a-102">ICorDebugFunctionBreakpoint::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="a616a-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="a616a-103">取得參考已設定中斷點之函數的 ICorDebugFunction 介面指標。</span><span class="sxs-lookup"><span data-stu-id="a616a-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a616a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a616a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a616a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a616a-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="a616a-106">脫銷設定中斷點之函式位址的指標。</span><span class="sxs-lookup"><span data-stu-id="a616a-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a616a-107">需求</span><span class="sxs-lookup"><span data-stu-id="a616a-107">Requirements</span></span>  
 <span data-ttu-id="a616a-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a616a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a616a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a616a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a616a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a616a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a616a-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a616a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
