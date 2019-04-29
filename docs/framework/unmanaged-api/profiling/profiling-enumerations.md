---
title: 分析列舉
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996352637f34b0b6c0d12e611a6d9e70ab85230e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757569"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="fdd48-102">分析列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-102">Profiling Enumerations</span></span>
<span data-ttu-id="fdd48-103">本節描述分析 API 所使用的 Unmanaged 列舉。</span><span class="sxs-lookup"><span data-stu-id="fdd48-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fdd48-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="fdd48-104">In This Section</span></span>  
 [<span data-ttu-id="fdd48-105">COR_PRF_CLAUSE_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="fdd48-106">指出剛輸入或留下的程式碼的 exception 子句類型。</span><span class="sxs-lookup"><span data-stu-id="fdd48-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="fdd48-107">COR_PRF_CODEGEN_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="fdd48-108">定義可以使用設定的程式碼產生旗標[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fdd48-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="fdd48-109">COR_PRF_FINALIZER_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="fdd48-110">描述物件的完成項。</span><span class="sxs-lookup"><span data-stu-id="fdd48-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="fdd48-111">COR_PRF_GC_GENERATION 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="fdd48-112">指出記憶體回收產生。</span><span class="sxs-lookup"><span data-stu-id="fdd48-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="fdd48-113">COR_PRF_GC_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="fdd48-114">指出正在發生之記憶體回收的原因。</span><span class="sxs-lookup"><span data-stu-id="fdd48-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="fdd48-115">COR_PRF_GC_ROOT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="fdd48-116">指出記憶體回收行程根目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="fdd48-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="fdd48-117">COR_PRF_GC_ROOT_KIND 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="fdd48-118">表示記憶體回收行程根目錄所公開的種類[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="fdd48-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="fdd48-119">COR_PRF_HIGH_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="fdd48-120">提供旗標，除了那些常見於[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別，可以指定程式碼剖析工具，以[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法載入時。</span><span class="sxs-lookup"><span data-stu-id="fdd48-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="fdd48-121">COR_PRF_JIT_CACHE 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="fdd48-122">指出快取的函式搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="fdd48-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="fdd48-123">COR_PRF_MISC 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="fdd48-124">包含指定特定識別項的常數值。</span><span class="sxs-lookup"><span data-stu-id="fdd48-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="fdd48-125">COR_PRF_MODULE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="fdd48-126">指定模組的屬性。</span><span class="sxs-lookup"><span data-stu-id="fdd48-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="fdd48-127">COR_PRF_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="fdd48-128">包含值，這些值用於指定分析工具想要訂閱的行為、功能或事件。</span><span class="sxs-lookup"><span data-stu-id="fdd48-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="fdd48-129">COR_PRF_RUNTIME_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="fdd48-130">包含值，這些值指出 Common Language Runtime 的版本。</span><span class="sxs-lookup"><span data-stu-id="fdd48-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="fdd48-131">COR_PRF_SNAPSHOT_INFO 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="fdd48-132">指定在每個分析工具的 `StackSnapshotCallback` 函式呼叫中，有多少資料要透過堆疊快照傳回。</span><span class="sxs-lookup"><span data-stu-id="fdd48-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="fdd48-133">COR_PRF_STATIC_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="fdd48-134">指出欄位是否為靜態，若是靜態，則欄位套用的是靜態品質。</span><span class="sxs-lookup"><span data-stu-id="fdd48-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="fdd48-135">COR_PRF_SUSPEND_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="fdd48-136">指出執行階段暫停的原因。</span><span class="sxs-lookup"><span data-stu-id="fdd48-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="fdd48-137">COR_PRF_TRANSITION_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="fdd48-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="fdd48-138">指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。</span><span class="sxs-lookup"><span data-stu-id="fdd48-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fdd48-139">相關章節</span><span class="sxs-lookup"><span data-stu-id="fdd48-139">Related Sections</span></span>  
 [<span data-ttu-id="fdd48-140">分析概觀</span><span class="sxs-lookup"><span data-stu-id="fdd48-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="fdd48-141">分析介面</span><span class="sxs-lookup"><span data-stu-id="fdd48-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="fdd48-142">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="fdd48-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="fdd48-143">分析結構</span><span class="sxs-lookup"><span data-stu-id="fdd48-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
