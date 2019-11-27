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
ms.openlocfilehash: c33a868b643cb3e3fd5dfaf436e3078bc590705c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449813"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="eec62-102">ICorProfilerInfo10：： RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="eec62-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="eec62-103">ReJITs 要求的方法，以及所要求之方法的任何 inliners。</span><span class="sxs-lookup"><span data-stu-id="eec62-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="eec62-104">語法</span><span class="sxs-lookup"><span data-stu-id="eec62-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

#### <a name="parameters"></a><span data-ttu-id="eec62-105">參數</span><span class="sxs-lookup"><span data-stu-id="eec62-105">Parameters</span></span>

`dwRejitFlags` \
<span data-ttu-id="eec62-106">在[COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md)的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="eec62-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>

`cFunctions` \
<span data-ttu-id="eec62-107">[in] 要重新編譯的函式數目。</span><span class="sxs-lookup"><span data-stu-id="eec62-107">[in] The number of functions to recompile.</span></span>

`moduleIds` \
<span data-ttu-id="eec62-108">[in] 指定 (`moduleId`, `module`) 組的 `methodDef` 部分，這個部分可識別所要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="eec62-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

`methodIds` \
<span data-ttu-id="eec62-109">[in] 指定 (`methodId`, `module`) 組的 `methodDef` 部分，這個部分可識別所要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="eec62-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="eec62-110">備註</span><span class="sxs-lookup"><span data-stu-id="eec62-110">Remarks</span></span>

<span data-ttu-id="eec62-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)不會對內嵌的方法進行任何追蹤。</span><span class="sxs-lookup"><span data-stu-id="eec62-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="eec62-112">分析工具預期會封鎖內嵌或追蹤內嵌，並為所有 inliners 呼叫 `RequestReJIT`，以確保內嵌方法的每個實例都已 ReJITted。</span><span class="sxs-lookup"><span data-stu-id="eec62-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="eec62-113">這會造成 ReJIT on attach 的問題，因為分析工具不存在來監視內嵌。</span><span class="sxs-lookup"><span data-stu-id="eec62-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="eec62-114">您可以呼叫這個方法，以確保一組完整的 inliners 也會 ReJITted。</span><span class="sxs-lookup"><span data-stu-id="eec62-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="eec62-115">需求</span><span class="sxs-lookup"><span data-stu-id="eec62-115">Requirements</span></span>

<span data-ttu-id="eec62-116">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="eec62-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="eec62-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eec62-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="eec62-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eec62-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="eec62-119">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eec62-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="eec62-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eec62-120">See also</span></span>

- [<span data-ttu-id="eec62-121">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="eec62-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
