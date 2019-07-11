---
title: ICorDebugFunctionBreakpoint::GetOffset 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67e71002a78023ad6e8ef89c7a57d484a65aaeb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756391"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="dab89-102">ICorDebugFunctionBreakpoint::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="dab89-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="dab89-103">取得中斷點的函式中的位移。</span><span class="sxs-lookup"><span data-stu-id="dab89-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab89-104">語法</span><span class="sxs-lookup"><span data-stu-id="dab89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dab89-105">參數</span><span class="sxs-lookup"><span data-stu-id="dab89-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="dab89-106">[out]中斷點的位移的指標。</span><span class="sxs-lookup"><span data-stu-id="dab89-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab89-107">需求</span><span class="sxs-lookup"><span data-stu-id="dab89-107">Requirements</span></span>  
 <span data-ttu-id="dab89-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dab89-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab89-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dab89-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dab89-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dab89-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dab89-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab89-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
