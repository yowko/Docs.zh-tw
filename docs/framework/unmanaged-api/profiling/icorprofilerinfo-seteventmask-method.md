---
title: ICorProfilerInfo::SetEventMask 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34aba20704ff8dc0d699ebee9440745d19c697b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566004"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="bef70-102">ICorProfilerInfo::SetEventMask 方法</span><span class="sxs-lookup"><span data-stu-id="bef70-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="bef70-103">設定一個值，以指定分析工具想要從通用語言執行平台 (CLR) 接收其通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="bef70-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef70-104">語法</span><span class="sxs-lookup"><span data-stu-id="bef70-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bef70-105">參數</span><span class="sxs-lookup"><span data-stu-id="bef70-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="bef70-106">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="bef70-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="bef70-107">每個位元分別控制不同的功能、行為或事件類型。</span><span class="sxs-lookup"><span data-stu-id="bef70-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="bef70-108">位元所述[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="bef70-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bef70-109">備註</span><span class="sxs-lookup"><span data-stu-id="bef70-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bef70-110">您應該呼叫[SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)而不是這個方法的方法。</span><span class="sxs-lookup"><span data-stu-id="bef70-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="bef70-111">雖然`SetEventMask`方法會繼續受到支援， [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)提供額外的功能。</span><span class="sxs-lookup"><span data-stu-id="bef70-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bef70-112">需求</span><span class="sxs-lookup"><span data-stu-id="bef70-112">Requirements</span></span>  
 <span data-ttu-id="bef70-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bef70-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bef70-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bef70-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bef70-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bef70-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bef70-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bef70-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef70-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bef70-117">See also</span></span>
- [<span data-ttu-id="bef70-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bef70-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="bef70-119">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="bef70-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
