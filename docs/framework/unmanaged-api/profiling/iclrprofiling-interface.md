---
title: ICLRProfiling 介面
ms.date: 03/30/2017
api_name:
- IClrProfiling
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling
helpviewer_keywords:
- IClrProfiling interface [.NET Framework profiling]
ms.assetid: 8b53ccc6-1b5e-4b30-a100-c9683d553f5a
topic_type:
- apiref
ms.openlocfilehash: 18cbaab08d5e3a5c36bec88ca5d5e48d1367444d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866737"
---
# <a name="iclrprofiling-interface"></a><span data-ttu-id="cb51a-102">ICLRProfiling 介面</span><span class="sxs-lookup"><span data-stu-id="cb51a-102">ICLRProfiling Interface</span></span>
<span data-ttu-id="cb51a-103">提供[ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)方法，可讓 profiler 附加至執行中的進程。</span><span class="sxs-lookup"><span data-stu-id="cb51a-103">Provides the [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb51a-104">方法</span><span class="sxs-lookup"><span data-stu-id="cb51a-104">Methods</span></span>  
  
|<span data-ttu-id="cb51a-105">方法</span><span class="sxs-lookup"><span data-stu-id="cb51a-105">Method</span></span>|<span data-ttu-id="cb51a-106">描述</span><span class="sxs-lookup"><span data-stu-id="cb51a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb51a-107">AttachProfiler 方法</span><span class="sxs-lookup"><span data-stu-id="cb51a-107">AttachProfiler Method</span></span>](iclrprofiling-attachprofiler-method.md)|<span data-ttu-id="cb51a-108">將指定的程式碼剖析工具附加至指定的處理序。</span><span class="sxs-lookup"><span data-stu-id="cb51a-108">Attaches the specified profiler to the specified process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb51a-109">備註</span><span class="sxs-lookup"><span data-stu-id="cb51a-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb51a-110">需求</span><span class="sxs-lookup"><span data-stu-id="cb51a-110">Requirements</span></span>  
 <span data-ttu-id="cb51a-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb51a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb51a-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb51a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb51a-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb51a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb51a-114">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb51a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb51a-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb51a-115">See also</span></span>

- [<span data-ttu-id="cb51a-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="cb51a-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cb51a-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="cb51a-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
