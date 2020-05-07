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
ms.openlocfilehash: af90886390b59932d3ae146a70fc2901ec1c378d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894660"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="6f520-102">ICorDebugBreakpointEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="6f520-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="6f520-103">從列舉中取得指定數目的 ICorDebugBreakpoint 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="6f520-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f520-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f520-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f520-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f520-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6f520-106">在要抓取的`ICorDebugBreakpoint`實例數目。</span><span class="sxs-lookup"><span data-stu-id="6f520-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="6f520-107">脫銷指標陣列，其中每一個都會指向代表中斷點的`ICorDebugBreakpoint`物件。</span><span class="sxs-lookup"><span data-stu-id="6f520-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6f520-108">脫銷實際傳回之`ICorDebugBreakpoint`實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="6f520-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="6f520-109">如果`celt`是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="6f520-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f520-110">需求</span><span class="sxs-lookup"><span data-stu-id="6f520-110">Requirements</span></span>  
 <span data-ttu-id="6f520-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f520-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f520-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f520-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f520-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f520-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f520-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f520-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
