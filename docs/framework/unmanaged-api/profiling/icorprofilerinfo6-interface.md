---
title: "ICorProfilerInfo6 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo6
api_location: mscorwks.dll
api_type: COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4ea37d277c3e8176e999de7c5bc527f2677cf25c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="bccff-102">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="bccff-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="bccff-103">[在.NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="bccff-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="bccff-104">子類別[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)可提供給定的 NGen 模組和內嵌指定的方法中所定義的所有方法的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bccff-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bccff-105">方法</span><span class="sxs-lookup"><span data-stu-id="bccff-105">Methods</span></span>  
  
|<span data-ttu-id="bccff-106">方法</span><span class="sxs-lookup"><span data-stu-id="bccff-106">Method</span></span>|<span data-ttu-id="bccff-107">說明</span><span class="sxs-lookup"><span data-stu-id="bccff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bccff-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法</span><span class="sxs-lookup"><span data-stu-id="bccff-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="bccff-109">傳回屬於指定的 NGen 模組，以及屬於給定方法主體中內嵌的所有方法的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bccff-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bccff-110">需求</span><span class="sxs-lookup"><span data-stu-id="bccff-110">Requirements</span></span>  
 <span data-ttu-id="bccff-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bccff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccff-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bccff-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bccff-113">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bccff-114">See Also</span></span>  
 [<span data-ttu-id="bccff-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="bccff-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
