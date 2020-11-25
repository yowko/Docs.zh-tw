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
ms.openlocfilehash: 38936a57944e9a0920c374f473c4cbe8e8d70abb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728663"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="cdc05-102">ICorDebugILCode::GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="cdc05-102">ICorDebugILCode::GetEHClauses Method</span></span>

<span data-ttu-id="cdc05-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="cdc05-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cdc05-104">傳回針對此中繼語言 (IL) 所定義之例外狀況處理 (EH) 子句清單的指標。</span><span class="sxs-lookup"><span data-stu-id="cdc05-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc05-105">語法</span><span class="sxs-lookup"><span data-stu-id="cdc05-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc05-106">參數</span><span class="sxs-lookup"><span data-stu-id="cdc05-106">Parameters</span></span>  

 `cClauses`  
 <span data-ttu-id="cdc05-107">[in] `clauses` 陣列的儲存體容量。</span><span class="sxs-lookup"><span data-stu-id="cdc05-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="cdc05-108">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="cdc05-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="cdc05-109">[out] 其資訊寫入至 `clauses` 陣列的子句數。</span><span class="sxs-lookup"><span data-stu-id="cdc05-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="cdc05-110">子句</span><span class="sxs-lookup"><span data-stu-id="cdc05-110">clauses</span></span>  
 <span data-ttu-id="cdc05-111">擴展 [CorDebugEHClause](cordebugehclause-structure.md) 物件的陣列，其中包含針對此 IL 定義之例外狀況處理子句的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cdc05-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdc05-112">備註</span><span class="sxs-lookup"><span data-stu-id="cdc05-112">Remarks</span></span>  

 <span data-ttu-id="cdc05-113">如果 `cClauses` 為0且 `pcClauses` 為非 **null**， `pcClauses` 則會設定為可用的例外狀況處理子句數目。</span><span class="sxs-lookup"><span data-stu-id="cdc05-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="cdc05-114">如果 `cClauses` 不是零，則代表 `clauses` 陣列的儲存體容量。</span><span class="sxs-lookup"><span data-stu-id="cdc05-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="cdc05-115">傳回方法時，`clauses` 會包含 `cClauses` 項目的最大值，且 `pcClauses` 會設為實際寫入至 `clauses` 陣列的子句數。</span><span class="sxs-lookup"><span data-stu-id="cdc05-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdc05-116">需求</span><span class="sxs-lookup"><span data-stu-id="cdc05-116">Requirements</span></span>  

 <span data-ttu-id="cdc05-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cdc05-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc05-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdc05-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdc05-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdc05-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdc05-120">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdc05-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc05-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdc05-121">See also</span></span>

- [<span data-ttu-id="cdc05-122">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="cdc05-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="cdc05-123">CorDebugEHClause 結構</span><span class="sxs-lookup"><span data-stu-id="cdc05-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="cdc05-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cdc05-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
