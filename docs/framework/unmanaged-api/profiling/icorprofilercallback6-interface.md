---
title: "ICorProfilerCallback6 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dca83aca3aee4a072e90793e1bb33526b6e5ebd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="10a05-102">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="10a05-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="10a05-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="10a05-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="10a05-104">子類別[ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)提供 common language runtime 用於通知分析工具組件載入的回撥方法。</span><span class="sxs-lookup"><span data-stu-id="10a05-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10a05-105">方法</span><span class="sxs-lookup"><span data-stu-id="10a05-105">Methods</span></span>  
  
|<span data-ttu-id="10a05-106">方法</span><span class="sxs-lookup"><span data-stu-id="10a05-106">Method</span></span>|<span data-ttu-id="10a05-107">說明</span><span class="sxs-lookup"><span data-stu-id="10a05-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10a05-108">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="10a05-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="10a05-109">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="10a05-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10a05-110">備註</span><span class="sxs-lookup"><span data-stu-id="10a05-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10a05-111">需求</span><span class="sxs-lookup"><span data-stu-id="10a05-111">Requirements</span></span>  
 <span data-ttu-id="10a05-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10a05-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10a05-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10a05-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10a05-114">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10a05-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a05-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10a05-115">See Also</span></span>  
 [<span data-ttu-id="10a05-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="10a05-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
