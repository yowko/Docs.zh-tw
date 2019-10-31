---
title: ICorProfilerInfo6 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: b1d31012662964132f8b65f030a062ae39ded56e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130362"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="23f34-102">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="23f34-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="23f34-103">[在 .NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="23f34-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="23f34-104">[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)的子類別，可為指定 NGen 模組中定義的所有方法提供列舉值，並內嵌指定的方法。</span><span class="sxs-lookup"><span data-stu-id="23f34-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23f34-105">方法</span><span class="sxs-lookup"><span data-stu-id="23f34-105">Methods</span></span>  
  
|<span data-ttu-id="23f34-106">方法</span><span class="sxs-lookup"><span data-stu-id="23f34-106">Method</span></span>|<span data-ttu-id="23f34-107">描述</span><span class="sxs-lookup"><span data-stu-id="23f34-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23f34-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法</span><span class="sxs-lookup"><span data-stu-id="23f34-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="23f34-109">針對屬於給定 NGen 模組並內嵌在指定方法主體中的所有方法，傳回列舉值。</span><span class="sxs-lookup"><span data-stu-id="23f34-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23f34-110">需求</span><span class="sxs-lookup"><span data-stu-id="23f34-110">Requirements</span></span>  
 <span data-ttu-id="23f34-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23f34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f34-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23f34-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23f34-113">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f34-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f34-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="23f34-114">See also</span></span>

- [<span data-ttu-id="23f34-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="23f34-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
