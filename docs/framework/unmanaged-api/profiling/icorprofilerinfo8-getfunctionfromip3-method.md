---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: df9ecc9bc355c12f993763820eb5065ba8bcc36b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855911"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="ef272-102">ICorProfilerInfo8：： GetFunctionFromIP3 方法</span><span class="sxs-lookup"><span data-stu-id="ef272-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="ef272-103">將 managed 程式碼指令指標對應至 FunctionID。</span><span class="sxs-lookup"><span data-stu-id="ef272-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="ef272-104">這個方法適用于動態和非動態方法。</span><span class="sxs-lookup"><span data-stu-id="ef272-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef272-105">語法</span><span class="sxs-lookup"><span data-stu-id="ef272-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

#### <a name="parameters"></a><span data-ttu-id="ef272-106">參數</span><span class="sxs-lookup"><span data-stu-id="ef272-106">Parameters</span></span>

`ip` \
<span data-ttu-id="ef272-107">在Managed 程式碼中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="ef272-107">[in] The instruction pointer in managed code.</span></span>

`pFunctionId` \
<span data-ttu-id="ef272-108">脫銷函數識別碼。</span><span class="sxs-lookup"><span data-stu-id="ef272-108">[out] The function ID.</span></span>

`pReJitId` \
<span data-ttu-id="ef272-109">脫銷函式之 JIT 重新編譯版本的識別。</span><span class="sxs-lookup"><span data-stu-id="ef272-109">[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef272-110">備註</span><span class="sxs-lookup"><span data-stu-id="ef272-110">Remarks</span></span>

<span data-ttu-id="ef272-111">這個方法適用于動態和非動態方法。</span><span class="sxs-lookup"><span data-stu-id="ef272-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="ef272-112">它是[GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)的超集合，僅適用于具有中繼資料的函式。</span><span class="sxs-lookup"><span data-stu-id="ef272-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef272-113">需求</span><span class="sxs-lookup"><span data-stu-id="ef272-113">Requirements</span></span>

<span data-ttu-id="ef272-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef272-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ef272-115">**標頭：** Corprof.idl .idl，Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="ef272-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ef272-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef272-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ef272-117">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ef272-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ef272-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef272-118">See also</span></span>

- [<span data-ttu-id="ef272-119">ICorProfilerInfo8 介面</span><span class="sxs-lookup"><span data-stu-id="ef272-119">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
