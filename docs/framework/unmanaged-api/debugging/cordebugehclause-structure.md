---
title: CorDebugEHClause 結構
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 839e698c8921f916fad174bae4f4cc8bb4d02994
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157322"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="4ae10-102">CorDebugEHClause 結構</span><span class="sxs-lookup"><span data-stu-id="4ae10-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="4ae10-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="4ae10-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4ae10-104">代表中繼語言 (IL) 程式碼給定片段的例外狀況處理 (EH) 子句。</span><span class="sxs-lookup"><span data-stu-id="4ae10-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae10-105">語法</span><span class="sxs-lookup"><span data-stu-id="4ae10-105">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="4ae10-106">成員</span><span class="sxs-lookup"><span data-stu-id="4ae10-106">Members</span></span>  
  
|<span data-ttu-id="4ae10-107">成員</span><span class="sxs-lookup"><span data-stu-id="4ae10-107">Member</span></span>|<span data-ttu-id="4ae10-108">描述</span><span class="sxs-lookup"><span data-stu-id="4ae10-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="4ae10-109">描述 EH 子句中之例外狀況資訊的位元欄位。</span><span class="sxs-lookup"><span data-stu-id="4ae10-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="4ae10-110">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="4ae10-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="4ae10-111">`try` 區塊從方法主體開頭位移的位元組數。</span><span class="sxs-lookup"><span data-stu-id="4ae10-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="4ae10-112">`try` 區塊的長度 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="4ae10-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="4ae10-113">此 `try` 區塊之處理常式的位置。</span><span class="sxs-lookup"><span data-stu-id="4ae10-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="4ae10-114">處理常式程式碼的大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="4ae10-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="4ae10-115">以類型為基礎之例外狀況處理常式的中繼資料 Token。</span><span class="sxs-lookup"><span data-stu-id="4ae10-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="4ae10-116">以篩選器為基礎之例外狀況處理常式自方法主體開頭位移的位元組數。</span><span class="sxs-lookup"><span data-stu-id="4ae10-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ae10-117">備註</span><span class="sxs-lookup"><span data-stu-id="4ae10-117">Remarks</span></span>  
 <span data-ttu-id="4ae10-118">陣列`CoreDebugEHClause`值由[GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4ae10-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="4ae10-119">EH 子句資訊以 CLI 規格定義。</span><span class="sxs-lookup"><span data-stu-id="4ae10-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="4ae10-120">如需詳細資訊，請參閱[標準 ECMA-355:通用語言基礎結構 (CLI)，第 6 版](https://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="4ae10-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="4ae10-121">`flags` 欄位可以包含下列旗標。</span><span class="sxs-lookup"><span data-stu-id="4ae10-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="4ae10-122">請注意，CorDebug.idl 或 CorDebug.h 中並未定義這些旗標。</span><span class="sxs-lookup"><span data-stu-id="4ae10-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="4ae10-123">旗標</span><span class="sxs-lookup"><span data-stu-id="4ae10-123">Flag</span></span>|<span data-ttu-id="4ae10-124">值</span><span class="sxs-lookup"><span data-stu-id="4ae10-124">Value</span></span>|<span data-ttu-id="4ae10-125">描述</span><span class="sxs-lookup"><span data-stu-id="4ae10-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="4ae10-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="4ae10-126">0x00000000</span></span>|<span data-ttu-id="4ae10-127">宣告類型的例外狀況子句。</span><span class="sxs-lookup"><span data-stu-id="4ae10-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="4ae10-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="4ae10-128">0x00000001</span></span>|<span data-ttu-id="4ae10-129">例外狀況篩選器與處理常式子句。</span><span class="sxs-lookup"><span data-stu-id="4ae10-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="4ae10-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="4ae10-130">0x00000002</span></span>|<span data-ttu-id="4ae10-131">`finally` 子句。</span><span class="sxs-lookup"><span data-stu-id="4ae10-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="4ae10-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="4ae10-132">0x00000004</span></span>|<span data-ttu-id="4ae10-133">錯誤子句 (`finally` 子句只會在擲出例外狀況時呼叫)。</span><span class="sxs-lookup"><span data-stu-id="4ae10-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ae10-134">需求</span><span class="sxs-lookup"><span data-stu-id="4ae10-134">Requirements</span></span>  
 <span data-ttu-id="4ae10-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ae10-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ae10-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ae10-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ae10-137">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ae10-137">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4ae10-138">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4ae10-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4ae10-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ae10-139">See also</span></span>

- [<span data-ttu-id="4ae10-140">GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="4ae10-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="4ae10-141">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="4ae10-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
