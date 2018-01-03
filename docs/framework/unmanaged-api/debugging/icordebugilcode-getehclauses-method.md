---
title: "ICorDebugILCode::GetEHClauses 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode.GetEHClauses
api_location: mscordbi.dll
api_type: COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32b3a7bf7edaf15e44ea65e2d3b4f5037add8d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="66529-102">ICorDebugILCode::GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="66529-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="66529-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="66529-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="66529-104">傳回針對此中繼語言 (IL) 所定義之例外狀況處理 (EH) 子句清單的指標。</span><span class="sxs-lookup"><span data-stu-id="66529-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66529-105">語法</span><span class="sxs-lookup"><span data-stu-id="66529-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66529-106">參數</span><span class="sxs-lookup"><span data-stu-id="66529-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="66529-107">[in] `clauses` 陣列的儲存容量。</span><span class="sxs-lookup"><span data-stu-id="66529-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="66529-108">如需詳細資訊，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="66529-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="66529-109">[out] 其資訊寫入至 `clauses` 陣列的子句數。</span><span class="sxs-lookup"><span data-stu-id="66529-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="66529-110">子句</span><span class="sxs-lookup"><span data-stu-id="66529-110">clauses</span></span>  
 <span data-ttu-id="66529-111">[out]陣列[CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)物件，其中包含有關例外狀況處理子句針對此 IL 定義。</span><span class="sxs-lookup"><span data-stu-id="66529-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66529-112">備註</span><span class="sxs-lookup"><span data-stu-id="66529-112">Remarks</span></span>  
 <span data-ttu-id="66529-113">如果`cClauses`為 0 和`pcClauses`是非**null**，`pcClauses`設為 可用的例外狀況處理子句數。</span><span class="sxs-lookup"><span data-stu-id="66529-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="66529-114">如果 `cClauses` 不是零，則代表 `clauses` 陣列的儲存體容量。</span><span class="sxs-lookup"><span data-stu-id="66529-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="66529-115">傳回方法時，`clauses` 會包含 `cClauses` 項目的最大值，且 `pcClauses` 會設為實際寫入至 `clauses` 陣列的子句數。</span><span class="sxs-lookup"><span data-stu-id="66529-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66529-116">需求</span><span class="sxs-lookup"><span data-stu-id="66529-116">Requirements</span></span>  
 <span data-ttu-id="66529-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66529-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66529-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66529-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66529-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66529-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66529-120">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66529-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66529-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="66529-121">See Also</span></span>  
 [<span data-ttu-id="66529-122">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="66529-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="66529-123">CorDebugEHClause 結構</span><span class="sxs-lookup"><span data-stu-id="66529-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [<span data-ttu-id="66529-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="66529-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
