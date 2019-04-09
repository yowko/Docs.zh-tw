---
title: ICorDebugILCode::GetEHClauses 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105050"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="87c29-102">ICorDebugILCode::GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="87c29-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="87c29-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="87c29-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="87c29-104">傳回針對此中繼語言 (IL) 所定義之例外狀況處理 (EH) 子句清單的指標。</span><span class="sxs-lookup"><span data-stu-id="87c29-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c29-105">語法</span><span class="sxs-lookup"><span data-stu-id="87c29-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87c29-106">參數</span><span class="sxs-lookup"><span data-stu-id="87c29-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="87c29-107">[in] `clauses` 陣列的儲存體容量。</span><span class="sxs-lookup"><span data-stu-id="87c29-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="87c29-108">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="87c29-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="87c29-109">[out] 其資訊寫入至 `clauses` 陣列的子句數。</span><span class="sxs-lookup"><span data-stu-id="87c29-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="87c29-110">子句</span><span class="sxs-lookup"><span data-stu-id="87c29-110">clauses</span></span>  
 <span data-ttu-id="87c29-111">[out]陣列[CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)包含有關例外狀況處理子句針對此 IL 定義的物件。</span><span class="sxs-lookup"><span data-stu-id="87c29-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87c29-112">備註</span><span class="sxs-lookup"><span data-stu-id="87c29-112">Remarks</span></span>  
 <span data-ttu-id="87c29-113">如果`cClauses`為 0 並`pcClauses`是非**null**，`pcClauses`設為 可用的例外狀況處理子句數。</span><span class="sxs-lookup"><span data-stu-id="87c29-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="87c29-114">如果 `cClauses` 不是零，則代表 `clauses` 陣列的儲存體容量。</span><span class="sxs-lookup"><span data-stu-id="87c29-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="87c29-115">傳回方法時，`clauses` 會包含 `cClauses` 項目的最大值，且 `pcClauses` 會設為實際寫入至 `clauses` 陣列的子句數。</span><span class="sxs-lookup"><span data-stu-id="87c29-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c29-116">需求</span><span class="sxs-lookup"><span data-stu-id="87c29-116">Requirements</span></span>  
 <span data-ttu-id="87c29-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87c29-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c29-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87c29-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87c29-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87c29-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="87c29-120">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="87c29-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87c29-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87c29-121">See also</span></span>

- [<span data-ttu-id="87c29-122">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="87c29-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="87c29-123">CorDebugEHClause 結構</span><span class="sxs-lookup"><span data-stu-id="87c29-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [<span data-ttu-id="87c29-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="87c29-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
