---
title: ICorProfilerInfo5 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: 655cdd5db0894a4e44d43b071caf1ee0829ffe50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861719"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="d7614-102">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="d7614-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="d7614-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="d7614-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d7614-104">[ICorProfilerInfo4](icorprofilerinfo4-interface.md)的子類別，提供程式碼分析工具用來與 common language RUNTIME （CLR）通訊以控制事件監視的方法。</span><span class="sxs-lookup"><span data-stu-id="d7614-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7614-105">方法</span><span class="sxs-lookup"><span data-stu-id="d7614-105">Methods</span></span>  
  
|<span data-ttu-id="d7614-106">方法</span><span class="sxs-lookup"><span data-stu-id="d7614-106">Method</span></span>|<span data-ttu-id="d7614-107">描述</span><span class="sxs-lookup"><span data-stu-id="d7614-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7614-108">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="d7614-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="d7614-109">取得分析工具想要從 CLR 接收的目前事件分類通知。</span><span class="sxs-lookup"><span data-stu-id="d7614-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="d7614-110">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="d7614-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="d7614-111">設定一個值，以指定分析工具想要從 CLR 接收事件通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="d7614-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7614-112">備註</span><span class="sxs-lookup"><span data-stu-id="d7614-112">Remarks</span></span>  
 <span data-ttu-id="d7614-113">此介面上可用的方法是用來取代[ICorProfilerInfo：： GetEventMask](icorprofilerinfo-geteventmask-method.md)和[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d7614-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7614-114">需求</span><span class="sxs-lookup"><span data-stu-id="d7614-114">Requirements</span></span>  
 <span data-ttu-id="d7614-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7614-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7614-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7614-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7614-117">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7614-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7614-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7614-118">See also</span></span>

- [<span data-ttu-id="d7614-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="d7614-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
