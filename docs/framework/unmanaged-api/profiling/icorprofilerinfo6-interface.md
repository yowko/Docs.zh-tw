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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: febe130b4d61b6179aeab3bfcd63891c38b13fbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128930"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="9cb43-102">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="9cb43-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="9cb43-103">[.NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="9cb43-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="9cb43-104">子類別[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) ，提供列舉值指定的 NGen 模組和內嵌指定的方法中所定義的所有方法。</span><span class="sxs-lookup"><span data-stu-id="9cb43-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9cb43-105">方法</span><span class="sxs-lookup"><span data-stu-id="9cb43-105">Methods</span></span>  
  
|<span data-ttu-id="9cb43-106">方法</span><span class="sxs-lookup"><span data-stu-id="9cb43-106">Method</span></span>|<span data-ttu-id="9cb43-107">描述</span><span class="sxs-lookup"><span data-stu-id="9cb43-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9cb43-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法</span><span class="sxs-lookup"><span data-stu-id="9cb43-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="9cb43-109">傳回屬於指定的 NGen 模組，以及屬於指定的方法主體中內嵌的所有方法的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9cb43-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cb43-110">需求</span><span class="sxs-lookup"><span data-stu-id="9cb43-110">Requirements</span></span>  
 <span data-ttu-id="9cb43-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cb43-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb43-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9cb43-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="9cb43-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9cb43-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9cb43-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cb43-114">See also</span></span>

- [<span data-ttu-id="9cb43-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="9cb43-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
