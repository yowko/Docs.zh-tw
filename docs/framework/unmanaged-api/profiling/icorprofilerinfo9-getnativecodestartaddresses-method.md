---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 99706fdc3d60a5e1a7f85400c1184d5acc808e42
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449722"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="cb9ad-102">ICorProfilerInfo9：： GetNativeCodeStartAddresses 方法</span><span class="sxs-lookup"><span data-stu-id="cb9ad-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="cb9ad-103">假設有 functionId 和 rejitId，會列舉此程式碼中所有目前存在之已編譯版本的原生程式碼起始位址。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb9ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb9ad-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="cb9ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb9ad-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="cb9ad-106">中的 \[] 應傳回其機器碼起始位址的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="cb9ad-107">\[in] JIT 重新編譯函式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="cb9ad-108">\[in] `codeStartAddresses` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="cb9ad-109">\[out] 可用的位址數目。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="cb9ad-110">\[out] `UINT_PTR`的陣列，其中每一個都是所指定函式的原生主體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb9ad-111">備註</span><span class="sxs-lookup"><span data-stu-id="cb9ad-111">Remarks</span></span>

<span data-ttu-id="cb9ad-112">啟用階層式編譯時，函數可能會有一個以上的機器碼主體。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb9ad-113">需求</span><span class="sxs-lookup"><span data-stu-id="cb9ad-113">Requirements</span></span>

<span data-ttu-id="cb9ad-114">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="cb9ad-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="cb9ad-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb9ad-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cb9ad-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb9ad-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cb9ad-117">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb9ad-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cb9ad-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb9ad-118">See also</span></span>

- [<span data-ttu-id="cb9ad-119">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="cb9ad-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
