---
title: "ICorDebugProcessEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 566d4a7eefee846f26abbc64f97e0063e847218b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="db30f-102">ICorDebugProcessEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="db30f-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="db30f-103">取得 ICorDebugProcess 執行個體的指定的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="db30f-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db30f-104">語法</span><span class="sxs-lookup"><span data-stu-id="db30f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db30f-105">參數</span><span class="sxs-lookup"><span data-stu-id="db30f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="db30f-106">[in]數目`ICorDebugProcess`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db30f-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processess`  
 <span data-ttu-id="db30f-107">[out]陣列的指標，其中每個指向`ICorDebugProcess`物件，表示處理程序。</span><span class="sxs-lookup"><span data-stu-id="db30f-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="db30f-108">[out]指標的數目`ICorDebugProcess`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db30f-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="db30f-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="db30f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db30f-110">需求</span><span class="sxs-lookup"><span data-stu-id="db30f-110">Requirements</span></span>  
 <span data-ttu-id="db30f-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db30f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db30f-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db30f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db30f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db30f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db30f-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db30f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
