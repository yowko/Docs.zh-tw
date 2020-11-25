---
title: ICorProfilerCallback6 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 2176b624a427994b9d2af4b5eba31a64c9288a0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725465"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="de300-102">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="de300-102">ICorProfilerCallback6 Interface</span></span>

<span data-ttu-id="de300-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="de300-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="de300-104">提供回呼方法的 [ICorProfilerCallback5](icorprofilercallback5-interface.md) 子類別，可讓 common language runtime 用來通知分析工具元件正在載入。</span><span class="sxs-lookup"><span data-stu-id="de300-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="de300-105">方法</span><span class="sxs-lookup"><span data-stu-id="de300-105">Methods</span></span>  
  
|<span data-ttu-id="de300-106">方法</span><span class="sxs-lookup"><span data-stu-id="de300-106">Method</span></span>|<span data-ttu-id="de300-107">描述</span><span class="sxs-lookup"><span data-stu-id="de300-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de300-108">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="de300-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="de300-109">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="de300-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de300-110">備註</span><span class="sxs-lookup"><span data-stu-id="de300-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de300-111">需求</span><span class="sxs-lookup"><span data-stu-id="de300-111">Requirements</span></span>  

 <span data-ttu-id="de300-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de300-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de300-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de300-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de300-114">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de300-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de300-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de300-115">See also</span></span>

- [<span data-ttu-id="de300-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="de300-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
