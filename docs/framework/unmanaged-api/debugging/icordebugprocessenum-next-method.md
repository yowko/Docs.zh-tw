---
title: ICorDebugProcessEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9f32b554de191ff84e7c319e2a00e3cd0610a9f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422203"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="6cfa3-102">ICorDebugProcessEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="6cfa3-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="6cfa3-103">取得指定的 ICorDebugProcess 執行個體的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="6cfa3-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cfa3-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cfa3-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cfa3-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cfa3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6cfa3-106">[in]數目`ICorDebugProcess`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6cfa3-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="6cfa3-107">[out]指標的陣列，其中每一個指向`ICorDebugProcess`物件，表示處理程序。</span><span class="sxs-lookup"><span data-stu-id="6cfa3-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6cfa3-108">[out]數目的指標`ICorDebugProcess`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6cfa3-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="6cfa3-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="6cfa3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cfa3-110">需求</span><span class="sxs-lookup"><span data-stu-id="6cfa3-110">Requirements</span></span>  
 <span data-ttu-id="6cfa3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cfa3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cfa3-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cfa3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cfa3-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cfa3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cfa3-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cfa3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
