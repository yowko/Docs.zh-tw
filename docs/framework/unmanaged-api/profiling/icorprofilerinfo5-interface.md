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
ms.openlocfilehash: 82f6262c2c576b49be4e7fcaa14043950df4c67a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495623"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="19113-102">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="19113-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="19113-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="19113-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="19113-104">[ICorProfilerInfo4](icorprofilerinfo4-interface.md)的子類別，提供程式碼分析工具用來與 common language RUNTIME （CLR）通訊以控制事件監視的方法。</span><span class="sxs-lookup"><span data-stu-id="19113-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19113-105">方法</span><span class="sxs-lookup"><span data-stu-id="19113-105">Methods</span></span>  
  
|<span data-ttu-id="19113-106">方法</span><span class="sxs-lookup"><span data-stu-id="19113-106">Method</span></span>|<span data-ttu-id="19113-107">描述</span><span class="sxs-lookup"><span data-stu-id="19113-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19113-108">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="19113-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="19113-109">取得分析工具想要從 CLR 接收的目前事件分類通知。</span><span class="sxs-lookup"><span data-stu-id="19113-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="19113-110">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="19113-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="19113-111">設定一個值，以指定分析工具想要從 CLR 接收事件通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="19113-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19113-112">備註</span><span class="sxs-lookup"><span data-stu-id="19113-112">Remarks</span></span>  
 <span data-ttu-id="19113-113">此介面上可用的方法是用來取代[ICorProfilerInfo：： GetEventMask](icorprofilerinfo-geteventmask-method.md)和[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="19113-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19113-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="19113-114">Requirements</span></span>  
 <span data-ttu-id="19113-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19113-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19113-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19113-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19113-117">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19113-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19113-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19113-118">See also</span></span>

- [<span data-ttu-id="19113-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="19113-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
