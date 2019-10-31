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
ms.openlocfilehash: db24228de7e8c98fd97f890b1e408515172299b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125663"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="79dfe-102">ICorDebugCode::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="79dfe-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="79dfe-103">取得指定函式的所有程式碼，格式化為可進行反組譯。</span><span class="sxs-lookup"><span data-stu-id="79dfe-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="79dfe-104">這個方法已在 .NET Framework 版本2.0 中被取代。</span><span class="sxs-lookup"><span data-stu-id="79dfe-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="79dfe-105">請改用[ICorDebugCode2：： GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="79dfe-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79dfe-106">語法</span><span class="sxs-lookup"><span data-stu-id="79dfe-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79dfe-107">參數</span><span class="sxs-lookup"><span data-stu-id="79dfe-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="79dfe-108">在函數開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="79dfe-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="79dfe-109">在函數結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="79dfe-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="79dfe-110">在將傳回程序代碼之 `buffer` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="79dfe-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="79dfe-111">脫銷將傳回程序代碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="79dfe-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="79dfe-112">脫銷傳回的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="79dfe-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79dfe-113">備註</span><span class="sxs-lookup"><span data-stu-id="79dfe-113">Remarks</span></span>  
 <span data-ttu-id="79dfe-114">如果函式的程式碼已分成多個區塊，則會以增加的原生位移順序串連它們。</span><span class="sxs-lookup"><span data-stu-id="79dfe-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="79dfe-115">不會檢查指令界限。</span><span class="sxs-lookup"><span data-stu-id="79dfe-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79dfe-116">需求</span><span class="sxs-lookup"><span data-stu-id="79dfe-116">Requirements</span></span>  
 <span data-ttu-id="79dfe-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79dfe-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79dfe-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79dfe-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79dfe-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79dfe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79dfe-120">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="79dfe-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79dfe-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="79dfe-121">See also</span></span>

- [<span data-ttu-id="79dfe-122">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="79dfe-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
