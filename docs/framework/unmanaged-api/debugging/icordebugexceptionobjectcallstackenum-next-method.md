---
title: ICorDebugExceptionObjectCallStackEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 6c742f541b358b40e6e2fd44ca437b0dd72e29b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091091"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="01085-102">ICorDebugExceptionObjectCallStackEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="01085-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="01085-103">取得指定的[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)實例數目，其中包含來自例外狀況物件之呼叫堆疊的資訊。</span><span class="sxs-lookup"><span data-stu-id="01085-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01085-104">語法</span><span class="sxs-lookup"><span data-stu-id="01085-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01085-105">參數</span><span class="sxs-lookup"><span data-stu-id="01085-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="01085-106">在要抓取的[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)實例數目。</span><span class="sxs-lookup"><span data-stu-id="01085-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="01085-107">脫銷指標陣列，其中每一個都會指向[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="01085-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="01085-108">脫銷實際傳回之[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="01085-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01085-109">備註</span><span class="sxs-lookup"><span data-stu-id="01085-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01085-110">需求</span><span class="sxs-lookup"><span data-stu-id="01085-110">Requirements</span></span>  
 <span data-ttu-id="01085-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01085-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01085-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01085-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01085-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01085-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01085-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01085-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01085-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="01085-115">See also</span></span>

- [<span data-ttu-id="01085-116">ICorDebugExceptionObjectCallStackEnum 介面</span><span class="sxs-lookup"><span data-stu-id="01085-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="01085-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="01085-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
