---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e3d5a09730cb8e477bd506749017a403acff1696
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540552"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="c9c67-102">ICorProfilerInfo10：： RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="c9c67-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="c9c67-103">ReJITs 所要求的方法，以及所要求之方法的任何 inliners。</span><span class="sxs-lookup"><span data-stu-id="c9c67-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9c67-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9c67-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="c9c67-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9c67-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="c9c67-106">\[in] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="c9c67-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="c9c67-107">\[in] 要重新編譯的函式數目。</span><span class="sxs-lookup"><span data-stu-id="c9c67-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="c9c67-108">\[in] 指定 `moduleId` (的部分 `module` ，) 組 `methodDef` 識別要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="c9c67-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="c9c67-109">\[in] 指定 `methodId` (的部分 `module` ，) 組 `methodDef` 識別要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="c9c67-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9c67-110">備註</span><span class="sxs-lookup"><span data-stu-id="c9c67-110">Remarks</span></span>

<span data-ttu-id="c9c67-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) 不會追蹤任何內嵌的方法。</span><span class="sxs-lookup"><span data-stu-id="c9c67-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="c9c67-112">分析工具預期會封鎖內嵌，或追蹤所有 inliners 的內嵌和呼叫， `RequestReJIT` 以確保已 ReJITted 內嵌方法的每個實例。</span><span class="sxs-lookup"><span data-stu-id="c9c67-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="c9c67-113">這對附加上的 ReJIT 造成問題，因為分析工具不存在來監視內嵌。</span><span class="sxs-lookup"><span data-stu-id="c9c67-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="c9c67-114">您可以呼叫這個方法，以保證一組完整的 inliners 也會 ReJITted。</span><span class="sxs-lookup"><span data-stu-id="c9c67-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9c67-115">需求</span><span class="sxs-lookup"><span data-stu-id="c9c67-115">Requirements</span></span>

<span data-ttu-id="c9c67-116">**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="c9c67-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="c9c67-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9c67-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c9c67-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9c67-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c9c67-119">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9c67-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c9c67-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9c67-120">See also</span></span>

- [<span data-ttu-id="c9c67-121">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="c9c67-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
