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
ms.openlocfilehash: a889d6ba00c4a0eb96a9923a7dbe52f3b93aaba5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795957"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="b423a-102">CorDebugEHClause 結構</span><span class="sxs-lookup"><span data-stu-id="b423a-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="b423a-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="b423a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b423a-104">代表中繼語言 (IL) 程式碼給定片段的例外狀況處理 (EH) 子句。</span><span class="sxs-lookup"><span data-stu-id="b423a-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b423a-105">語法</span><span class="sxs-lookup"><span data-stu-id="b423a-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b423a-106">成員</span><span class="sxs-lookup"><span data-stu-id="b423a-106">Members</span></span>  
  
|<span data-ttu-id="b423a-107">member</span><span class="sxs-lookup"><span data-stu-id="b423a-107">Member</span></span>|<span data-ttu-id="b423a-108">說明</span><span class="sxs-lookup"><span data-stu-id="b423a-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="b423a-109">描述 EH 子句中之例外狀況資訊的位元欄位。</span><span class="sxs-lookup"><span data-stu-id="b423a-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="b423a-110">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="b423a-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="b423a-111">`try` 區塊從方法主體開頭位移的位元組數。</span><span class="sxs-lookup"><span data-stu-id="b423a-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="b423a-112">`try` 區塊的長度 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="b423a-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="b423a-113">此 `try` 區塊之處理常式的位置。</span><span class="sxs-lookup"><span data-stu-id="b423a-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="b423a-114">處理常式程式碼的大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="b423a-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="b423a-115">以類型為基礎之例外狀況處理常式的中繼資料 Token。</span><span class="sxs-lookup"><span data-stu-id="b423a-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="b423a-116">以篩選器為基礎之例外狀況處理常式自方法主體開頭位移的位元組數。</span><span class="sxs-lookup"><span data-stu-id="b423a-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b423a-117">備註</span><span class="sxs-lookup"><span data-stu-id="b423a-117">Remarks</span></span>  
 <span data-ttu-id="b423a-118">GetEHClauses 方法會`CoreDebugEHClause`傳回值的陣列。 [GetEHClauses](icordebugilcode-getehclauses-method.md)</span><span class="sxs-lookup"><span data-stu-id="b423a-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="b423a-119">EH 子句資訊以 CLI 規格定義。</span><span class="sxs-lookup"><span data-stu-id="b423a-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="b423a-120">如需詳細資訊，請參閱[標準 ECMA-355：通用語言基礎結構（CLI）、第6版](https://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="b423a-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="b423a-121">`flags` 欄位可以包含下列旗標。</span><span class="sxs-lookup"><span data-stu-id="b423a-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="b423a-122">請注意，CorDebug.idl 或 CorDebug.h 中並未定義這些旗標。</span><span class="sxs-lookup"><span data-stu-id="b423a-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="b423a-123">旗標</span><span class="sxs-lookup"><span data-stu-id="b423a-123">Flag</span></span>|<span data-ttu-id="b423a-124">值</span><span class="sxs-lookup"><span data-stu-id="b423a-124">Value</span></span>|<span data-ttu-id="b423a-125">說明</span><span class="sxs-lookup"><span data-stu-id="b423a-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="b423a-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="b423a-126">0x00000000</span></span>|<span data-ttu-id="b423a-127">宣告類型的例外狀況子句。</span><span class="sxs-lookup"><span data-stu-id="b423a-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="b423a-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="b423a-128">0x00000001</span></span>|<span data-ttu-id="b423a-129">例外狀況篩選器與處理常式子句。</span><span class="sxs-lookup"><span data-stu-id="b423a-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="b423a-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="b423a-130">0x00000002</span></span>|<span data-ttu-id="b423a-131">`finally` 子句。</span><span class="sxs-lookup"><span data-stu-id="b423a-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="b423a-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="b423a-132">0x00000004</span></span>|<span data-ttu-id="b423a-133">錯誤子句 (`finally` 子句只會在擲出例外狀況時呼叫)。</span><span class="sxs-lookup"><span data-stu-id="b423a-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b423a-134">需求</span><span class="sxs-lookup"><span data-stu-id="b423a-134">Requirements</span></span>  
 <span data-ttu-id="b423a-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b423a-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b423a-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b423a-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b423a-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b423a-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b423a-138">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b423a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b423a-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="b423a-139">See also</span></span>

- [<span data-ttu-id="b423a-140">GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="b423a-140">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="b423a-141">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="b423a-141">Debugging Structures</span></span>](debugging-structures.md)
