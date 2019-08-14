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
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973978"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="39ec0-102">ICorProfilerInfo10:: RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="39ec0-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>
  
<span data-ttu-id="39ec0-103">ReJITs 要求的方法, 以及所要求之方法的任何 inliners。</span><span class="sxs-lookup"><span data-stu-id="39ec0-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="39ec0-104">語法</span><span class="sxs-lookup"><span data-stu-id="39ec0-104">Syntax</span></span>  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="39ec0-105">參數</span><span class="sxs-lookup"><span data-stu-id="39ec0-105">Parameters</span></span>  
 
 `dwRejitFlags` \
 <span data-ttu-id="39ec0-106">在[COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md)的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="39ec0-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>
 
 `cFunctions`  
 <span data-ttu-id="39ec0-107">[in] 要重新編譯的函式數目。</span><span class="sxs-lookup"><span data-stu-id="39ec0-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="39ec0-108">[in] 指定 (`module`, `methodDef`) 組的 `moduleId` 部分，這個部分可識別所要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="39ec0-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="39ec0-109">[in] 指定 (`module`, `methodDef`) 組的 `methodId` 部分，這個部分可識別所要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="39ec0-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  

## <a name="remarks"></a><span data-ttu-id="39ec0-110">備註</span><span class="sxs-lookup"><span data-stu-id="39ec0-110">Remarks</span></span>  
  <span data-ttu-id="39ec0-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)不會對內嵌的方法進行任何追蹤。</span><span class="sxs-lookup"><span data-stu-id="39ec0-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="39ec0-112">分析工具預期會封鎖內嵌或追蹤內嵌, 並針對所有`RequestReJIT` inliners 呼叫, 以確保內嵌方法的每個實例都已 ReJITted。</span><span class="sxs-lookup"><span data-stu-id="39ec0-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="39ec0-113">這會造成 ReJIT on attach 的問題, 因為分析工具不存在來監視內嵌。</span><span class="sxs-lookup"><span data-stu-id="39ec0-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="39ec0-114">您可以呼叫這個方法, 以確保一組完整的 inliners 也會 ReJITted。</span><span class="sxs-lookup"><span data-stu-id="39ec0-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>  

## <a name="requirements"></a><span data-ttu-id="39ec0-115">需求</span><span class="sxs-lookup"><span data-stu-id="39ec0-115">Requirements</span></span>  
 <span data-ttu-id="39ec0-116">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="39ec0-116">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="39ec0-117">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="39ec0-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="39ec0-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39ec0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39ec0-119">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39ec0-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="39ec0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39ec0-120">See also</span></span>
- [<span data-ttu-id="39ec0-121">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="39ec0-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

