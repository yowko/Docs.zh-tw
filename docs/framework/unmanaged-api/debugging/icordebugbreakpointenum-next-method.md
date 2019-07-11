---
title: ICorDebugBreakpointEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87249dae0eff4ea4899a63c0d13e79c266df453a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745002"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="b1bfc-102">ICorDebugBreakpointEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="b1bfc-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="b1bfc-103">取得指定的 ICorDebugBreakpoint 執行個體的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="b1bfc-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bfc-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1bfc-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1bfc-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1bfc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b1bfc-106">[in]數目`ICorDebugBreakpoint`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1bfc-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="b1bfc-107">[out]指標的陣列，其中每一個指向`ICorDebugBreakpoint`物件，表示中斷點。</span><span class="sxs-lookup"><span data-stu-id="b1bfc-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b1bfc-108">[out]數目的指標`ICorDebugBreakpoint`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1bfc-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="b1bfc-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="b1bfc-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bfc-110">需求</span><span class="sxs-lookup"><span data-stu-id="b1bfc-110">Requirements</span></span>  
 <span data-ttu-id="b1bfc-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bfc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bfc-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1bfc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1bfc-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1bfc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1bfc-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1bfc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
