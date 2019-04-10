---
title: ICorDebugCode::GetCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f396881ef16f63eaf198aec168e5e94ed887698b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228532"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="414ec-102">ICorDebugCode::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="414ec-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="414ec-103">取得指定的函式，針對 反組譯碼格式化的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="414ec-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="414ec-104">這個方法已被取代，在.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="414ec-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="414ec-105">使用[ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="414ec-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="414ec-106">語法</span><span class="sxs-lookup"><span data-stu-id="414ec-106">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="414ec-107">參數</span><span class="sxs-lookup"><span data-stu-id="414ec-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="414ec-108">[in]函式開頭位移。</span><span class="sxs-lookup"><span data-stu-id="414ec-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="414ec-109">[in]函式結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="414ec-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="414ec-110">[in]大小`buffer`到程式碼會傳回陣列。</span><span class="sxs-lookup"><span data-stu-id="414ec-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="414ec-111">[out]陣列，將在其中傳回的程式碼。</span><span class="sxs-lookup"><span data-stu-id="414ec-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="414ec-112">[out]傳回的位元組數。</span><span class="sxs-lookup"><span data-stu-id="414ec-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="414ec-113">備註</span><span class="sxs-lookup"><span data-stu-id="414ec-113">Remarks</span></span>  
 <span data-ttu-id="414ec-114">如果函式的程式碼，而且已經分割成多個區塊，串連這些區塊是以遞增的原生位移的順序。</span><span class="sxs-lookup"><span data-stu-id="414ec-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="414ec-115">不會檢查指令界限。</span><span class="sxs-lookup"><span data-stu-id="414ec-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="414ec-116">需求</span><span class="sxs-lookup"><span data-stu-id="414ec-116">Requirements</span></span>  
 <span data-ttu-id="414ec-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="414ec-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="414ec-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="414ec-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="414ec-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="414ec-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="414ec-120">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="414ec-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="414ec-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="414ec-121">See also</span></span>

- [<span data-ttu-id="414ec-122">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="414ec-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
