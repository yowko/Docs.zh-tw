---
title: "ICorDebugExceptionObjectCallStackEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum::Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a5d17bc46f6c2cab0d0d44f42e7b4741f67dbc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="ac853-102">ICorDebugExceptionObjectCallStackEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="ac853-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="ac853-103">取得指定的數目[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)包含來自例外狀況物件的呼叫堆疊資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac853-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac853-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac853-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac853-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac853-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ac853-106">[in]數目[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac853-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="ac853-107">[out]陣列的指標，其中每個指向[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="ac853-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ac853-108">[out]數目的指標[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac853-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac853-109">備註</span><span class="sxs-lookup"><span data-stu-id="ac853-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac853-110">需求</span><span class="sxs-lookup"><span data-stu-id="ac853-110">Requirements</span></span>  
 <span data-ttu-id="ac853-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac853-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac853-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac853-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac853-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac853-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac853-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac853-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac853-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac853-115">See Also</span></span>  
 [<span data-ttu-id="ac853-116">ICorDebugExceptionObjectCallStackEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ac853-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 [<span data-ttu-id="ac853-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ac853-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
