---
title: ICorProfilerInfo::SetILInstrumentedCodeMap 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65eee2e834251817b461f1cd1debf212696d5a5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855701"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="42d1b-102">ICorProfilerInfo::SetILInstrumentedCodeMap 方法</span><span class="sxs-lookup"><span data-stu-id="42d1b-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="42d1b-103">使用指定的 Microsoft 中繼語言（MSIL）對應專案，為指定的函式設定 Code Map。</span><span class="sxs-lookup"><span data-stu-id="42d1b-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="42d1b-104">在 .NET Framework 版本2.0 中，在`SetILInstrumentedCodeMap`代表特定`FunctionID`應用程式域中泛型函式的上呼叫會影響應用程式域中該函式的所有實例。</span><span class="sxs-lookup"><span data-stu-id="42d1b-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="42d1b-105">語法</span><span class="sxs-lookup"><span data-stu-id="42d1b-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="42d1b-106">參數</span><span class="sxs-lookup"><span data-stu-id="42d1b-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="42d1b-107">在要設定 Code Map 的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="42d1b-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="42d1b-108">在布林值，指出對`SetILInstrumentedCodeMap`方法的呼叫是否為特定`FunctionID`的第一個。</span><span class="sxs-lookup"><span data-stu-id="42d1b-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="42d1b-109">`fStartJit` `false` `true` 在第`FunctionID`一次呼叫給定的時，將設為，並在之後設定為。`SetILInstrumentedCodeMap`</span><span class="sxs-lookup"><span data-stu-id="42d1b-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="42d1b-110">在`cILMapEntries`陣列中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="42d1b-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="42d1b-111">在COR_IL_MAP 結構的陣列，其中每一個都會指定一個 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="42d1b-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="42d1b-112">備註</span><span class="sxs-lookup"><span data-stu-id="42d1b-112">Remarks</span></span>

<span data-ttu-id="42d1b-113">分析工具通常會在方法的原始程式碼中插入語句，以檢測該方法（例如，在到達指定的原始程式列時通知）。</span><span class="sxs-lookup"><span data-stu-id="42d1b-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="42d1b-114">`SetILInstrumentedCodeMap`可讓分析工具將原始 MSIL 指令對應至其新位置。</span><span class="sxs-lookup"><span data-stu-id="42d1b-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="42d1b-115">分析工具可以使用[ICorProfilerInfo：： GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)方法來取得給定原生位移的原始 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="42d1b-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="42d1b-116">偵錯工具會假設每個舊的位移都是指原始、未修改的 MSIL 程式碼內的 MSIL 位移，而且每個新的位移都會參考新檢測的程式碼內的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="42d1b-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="42d1b-117">對應應該以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="42d1b-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="42d1b-118">若要讓逐步執行正常運作，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="42d1b-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="42d1b-119">請勿重新排列已檢測的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="42d1b-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="42d1b-120">請勿移除原始的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="42d1b-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="42d1b-121">在對應的程式資料庫（PDB）檔案中包含所有順序點的專案。</span><span class="sxs-lookup"><span data-stu-id="42d1b-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="42d1b-122">對應不會插補遺漏的專案。</span><span class="sxs-lookup"><span data-stu-id="42d1b-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="42d1b-123">因此，假設有下列對應：</span><span class="sxs-lookup"><span data-stu-id="42d1b-123">So, given the following map:</span></span>

  <span data-ttu-id="42d1b-124">（0舊，0個新的）</span><span class="sxs-lookup"><span data-stu-id="42d1b-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="42d1b-125">（5個或10個新的）</span><span class="sxs-lookup"><span data-stu-id="42d1b-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="42d1b-126">（9個舊，20個新的）</span><span class="sxs-lookup"><span data-stu-id="42d1b-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="42d1b-127">舊的位移為0、1、2、3或4，將會對應至新的位移0。</span><span class="sxs-lookup"><span data-stu-id="42d1b-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="42d1b-128">舊的位移5、6、7或8會對應到新的位移10。</span><span class="sxs-lookup"><span data-stu-id="42d1b-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="42d1b-129">舊的位移9或更高版本會對應到新的位移20。</span><span class="sxs-lookup"><span data-stu-id="42d1b-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="42d1b-130">新的位移為0、1、2、3、4、5、6、7、8或9，將會對應到舊的位移0。</span><span class="sxs-lookup"><span data-stu-id="42d1b-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="42d1b-131">10、11、12、13、14、15、16、17、18或19的新位移會對應到舊的位移5。</span><span class="sxs-lookup"><span data-stu-id="42d1b-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="42d1b-132">新的位移20或以上會對應到舊的位移9。</span><span class="sxs-lookup"><span data-stu-id="42d1b-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="42d1b-133">在 .NET Framework 3.5 和之前的版本中，您可以`rgILMapEntries`呼叫[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)方法來配置陣列。</span><span class="sxs-lookup"><span data-stu-id="42d1b-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="42d1b-134">由於執行時間會取得此記憶體的擁有權，因此分析工具不應該嘗試釋放它。</span><span class="sxs-lookup"><span data-stu-id="42d1b-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="42d1b-135">需求</span><span class="sxs-lookup"><span data-stu-id="42d1b-135">Requirements</span></span>

<span data-ttu-id="42d1b-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42d1b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="42d1b-137">**標頭：** Corprof.idl .idl，Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="42d1b-137">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="42d1b-138">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42d1b-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="42d1b-139">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42d1b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="42d1b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42d1b-140">See also</span></span>

- [<span data-ttu-id="42d1b-141">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="42d1b-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
