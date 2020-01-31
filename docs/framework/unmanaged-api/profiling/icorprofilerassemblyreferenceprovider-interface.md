---
title: ICorProfilerAssemblyReferenceProvider 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: 13a298451c3e8e1c5809cc1cb222acb5ab85714b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866685"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="f0342-102">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="f0342-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="f0342-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="f0342-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f0342-104">可讓分析工具通知 common language runtime （CLR）程式碼剖析工具將在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼中新增的元件參考。</span><span class="sxs-lookup"><span data-stu-id="f0342-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0342-105">方法</span><span class="sxs-lookup"><span data-stu-id="f0342-105">Methods</span></span>  
  
|<span data-ttu-id="f0342-106">方法</span><span class="sxs-lookup"><span data-stu-id="f0342-106">Method</span></span>|<span data-ttu-id="f0342-107">描述</span><span class="sxs-lookup"><span data-stu-id="f0342-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0342-108">AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="f0342-108">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="f0342-109">通知 CLR 元件參考，分析工具計畫要在[ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼中加入。</span><span class="sxs-lookup"><span data-stu-id="f0342-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0342-110">備註</span><span class="sxs-lookup"><span data-stu-id="f0342-110">Remarks</span></span>  
 <span data-ttu-id="f0342-111">CLR 會在[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回呼中，將 `ICorProfilerAssemblyReferenceProvider` 介面物件傳遞給 profiler。</span><span class="sxs-lookup"><span data-stu-id="f0342-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="f0342-112">這可讓分析工具通知元件參考的 CLR，分析工具計畫稍後要在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)中新增。</span><span class="sxs-lookup"><span data-stu-id="f0342-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="f0342-113">回呼中。</span><span class="sxs-lookup"><span data-stu-id="f0342-113">callback.</span></span> <span data-ttu-id="f0342-114">這會增進 CLR 組件參考結束查核器及其演算法的精確度，以判定組件是否可以共用。</span><span class="sxs-lookup"><span data-stu-id="f0342-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="f0342-115">這個介面只能用在將此介面物件傳遞至分析工具的[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回呼中。</span><span class="sxs-lookup"><span data-stu-id="f0342-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0342-116">需求</span><span class="sxs-lookup"><span data-stu-id="f0342-116">Requirements</span></span>  
 <span data-ttu-id="f0342-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0342-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0342-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0342-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0342-119">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0342-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0342-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0342-120">See also</span></span>

- [<span data-ttu-id="f0342-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="f0342-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
