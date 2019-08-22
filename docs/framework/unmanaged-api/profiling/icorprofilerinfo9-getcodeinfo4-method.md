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
ms.openlocfilehash: e6708971909c1035e41786f4d8dad1cf9afdffaf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665621"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="decd4-102">ICorProfilerInfo9:: GetCodeInfo4 方法</span><span class="sxs-lookup"><span data-stu-id="decd4-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="decd4-103">假設機器碼的起始位址, 會傳回儲存此程式碼的虛擬記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="decd4-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="decd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="decd4-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

#### <a name="parameters"></a><span data-ttu-id="decd4-105">參數</span><span class="sxs-lookup"><span data-stu-id="decd4-105">Parameters</span></span>

`pNativeCodeStartAddress` \
<span data-ttu-id="decd4-106">在原生函式開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="decd4-106">[in] A pointer to the start of a native function.</span></span>

`cCodeInfos` \
<span data-ttu-id="decd4-107">[in] `codeInfos` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="decd4-107">[in] The size of the `codeInfos` array.</span></span>

`pcCodeInfos` \
<span data-ttu-id="decd4-108">脫銷可用[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構總數的指標。</span><span class="sxs-lookup"><span data-stu-id="decd4-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>

`codeInfos` \
<span data-ttu-id="decd4-109">[out] 呼叫者提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="decd4-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="decd4-110">方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。</span><span class="sxs-lookup"><span data-stu-id="decd4-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="decd4-111">備註</span><span class="sxs-lookup"><span data-stu-id="decd4-111">Remarks</span></span>

<span data-ttu-id="decd4-112">`GetCodeInfo4`方法類似于 [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), 不同之處在于它可以查閱方法的不同原生版本的程式碼資訊。</span><span class="sxs-lookup"><span data-stu-id="decd4-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="decd4-113">`GetCodeInfo4`可以觸發垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="decd4-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="decd4-114">範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。</span><span class="sxs-lookup"><span data-stu-id="decd4-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="decd4-115">傳回`GetCodeInfo4`之後, 您必須確認`codeInfos`緩衝區夠大, 足以包含所有的[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="decd4-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="decd4-116">若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="decd4-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="decd4-117">如果`cCodeInfos`除以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `codeInfos` `cCodeInfos`結構的大小小於`GetCodeInfo4` , 請配置較大的緩衝區, 以新的、較大的大小來更新, 然後再呼叫一次。 `pcCodeInfos`</span><span class="sxs-lookup"><span data-stu-id="decd4-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="decd4-118">或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo4`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="decd4-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="decd4-119">接著, 您可以將`codeInfos`緩衝區大小設定為中`pcCodeInfos`傳回的值, 乘以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構的大小, 然後再呼叫`GetCodeInfo4`一次。</span><span class="sxs-lookup"><span data-stu-id="decd4-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="decd4-120">需求</span><span class="sxs-lookup"><span data-stu-id="decd4-120">Requirements</span></span>

<span data-ttu-id="decd4-121">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="decd4-121">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="decd4-122">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="decd4-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="decd4-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="decd4-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="decd4-124">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="decd4-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="decd4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="decd4-125">See also</span></span>

- [<span data-ttu-id="decd4-126">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="decd4-126">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)
