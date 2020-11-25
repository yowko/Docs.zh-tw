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
ms.openlocfilehash: b3aed97e19694675fd5e0c1070dbbf6d9321eedd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733837"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="a14e3-102">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="a14e3-102">ICorProfilerInfo6 Interface</span></span>

<span data-ttu-id="a14e3-103">[在 .NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="a14e3-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="a14e3-104">[ICorProfilerInfo5](icorprofilerinfo5-interface.md)的子類別，提供指定之 NGen 模組中定義之所有方法的列舉值，並內嵌指定的方法。</span><span class="sxs-lookup"><span data-stu-id="a14e3-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a14e3-105">方法</span><span class="sxs-lookup"><span data-stu-id="a14e3-105">Methods</span></span>  
  
|<span data-ttu-id="a14e3-106">方法</span><span class="sxs-lookup"><span data-stu-id="a14e3-106">Method</span></span>|<span data-ttu-id="a14e3-107">描述</span><span class="sxs-lookup"><span data-stu-id="a14e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a14e3-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法</span><span class="sxs-lookup"><span data-stu-id="a14e3-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="a14e3-109">針對屬於指定之 NGen 模組的所有方法，以及在指定方法主體內內嵌的所有方法，傳回列舉值。</span><span class="sxs-lookup"><span data-stu-id="a14e3-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a14e3-110">需求</span><span class="sxs-lookup"><span data-stu-id="a14e3-110">Requirements</span></span>  

 <span data-ttu-id="a14e3-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a14e3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a14e3-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a14e3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a14e3-113">**.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a14e3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14e3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a14e3-114">See also</span></span>

- [<span data-ttu-id="a14e3-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="a14e3-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
