---
title: "ICorDebugCode::GetCode 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f906fddf8073a00d2a3741613aae537b8604af67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="e3507-102">ICorDebugCode::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="e3507-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="e3507-103">取得指定的函式，格式為反組譯碼的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="e3507-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="e3507-104">.NET Framework 2.0 版中，這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="e3507-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e3507-105">使用[icordebugcode2:: Getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="e3507-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3507-106">語法</span><span class="sxs-lookup"><span data-stu-id="e3507-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e3507-107">參數</span><span class="sxs-lookup"><span data-stu-id="e3507-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="e3507-108">[in]函式開頭位移。</span><span class="sxs-lookup"><span data-stu-id="e3507-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="e3507-109">[in]在函式結束位移。</span><span class="sxs-lookup"><span data-stu-id="e3507-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="e3507-110">[in]大小`buffer`到程式碼傳回的陣列。</span><span class="sxs-lookup"><span data-stu-id="e3507-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e3507-111">[out]程式碼會傳回所在陣列。</span><span class="sxs-lookup"><span data-stu-id="e3507-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="e3507-112">[out]傳回的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="e3507-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3507-113">備註</span><span class="sxs-lookup"><span data-stu-id="e3507-113">Remarks</span></span>  
 <span data-ttu-id="e3507-114">如果函式的程式碼，而且已經分割成多個區塊，串連這些區塊是以遞增的原生位移的順序。</span><span class="sxs-lookup"><span data-stu-id="e3507-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="e3507-115">不檢查指令界限。</span><span class="sxs-lookup"><span data-stu-id="e3507-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3507-116">需求</span><span class="sxs-lookup"><span data-stu-id="e3507-116">Requirements</span></span>  
 <span data-ttu-id="e3507-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3507-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3507-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3507-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3507-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3507-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3507-120">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="e3507-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3507-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="e3507-121">See Also</span></span>  
 [<span data-ttu-id="e3507-122">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="e3507-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
