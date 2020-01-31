---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3e3e3afc221d153ff3573126ff10014d39af761a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868300"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="e5cc6-102">ICorProfilerInfo9：： GetCodeInfo4 方法</span><span class="sxs-lookup"><span data-stu-id="e5cc6-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="e5cc6-103">假設機器碼的起始位址，會傳回儲存此程式碼的虛擬記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5cc6-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5cc6-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="e5cc6-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5cc6-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="e5cc6-106">中的 \[]：原生函式開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="e5cc6-107">\[in] `codeInfos` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="e5cc6-108">\[out] 可用[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構總數的指標。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="e5cc6-109">\[out] 呼叫端提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="e5cc6-110">方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5cc6-111">備註</span><span class="sxs-lookup"><span data-stu-id="e5cc6-111">Remarks</span></span>

<span data-ttu-id="e5cc6-112">`GetCodeInfo4`方法類似于 [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), 不同之處在于它可以查閱方法的不同原生版本的程式碼資訊。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="e5cc6-113">`GetCodeInfo4` 可以觸發垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="e5cc6-114">範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="e5cc6-115">`GetCodeInfo4` 傳回之後，您必須確認 `codeInfos` 緩衝區夠大，足以包含所有[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="e5cc6-116">若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e5cc6-117">如果 `cCodeInfos` 除以[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構的大小小於 `pcCodeInfos`，請配置較大的 `codeInfos` 緩衝區、以新的、較大的大小更新 `cCodeInfos`，然後再次呼叫 `GetCodeInfo4`。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="e5cc6-118">或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo4`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e5cc6-119">接著，您可以將 `codeInfos` 緩衝區大小設定為 `pcCodeInfos`中傳回的值，乘以[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構的大小，然後再次呼叫 `GetCodeInfo4`。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5cc6-120">需求</span><span class="sxs-lookup"><span data-stu-id="e5cc6-120">Requirements</span></span>

<span data-ttu-id="e5cc6-121">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="e5cc6-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="e5cc6-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5cc6-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e5cc6-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5cc6-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e5cc6-124">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5cc6-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e5cc6-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5cc6-125">See also</span></span>

- [<span data-ttu-id="e5cc6-126">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="e5cc6-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
