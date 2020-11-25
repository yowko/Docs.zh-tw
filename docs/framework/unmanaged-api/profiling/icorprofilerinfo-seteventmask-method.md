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
ms.openlocfilehash: 9d319b6523b2c2a1bcc5cb6ea7a28efa67d898e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720941"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="fd887-102">ICorProfilerInfo::SetEventMask 方法</span><span class="sxs-lookup"><span data-stu-id="fd887-102">ICorProfilerInfo::SetEventMask Method</span></span>

<span data-ttu-id="fd887-103">設定一個值，以指定分析工具想要從通用語言執行平台 (CLR) 接收其通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="fd887-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd887-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd887-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd887-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd887-105">Parameters</span></span>  

 `dwEvents`  
 <span data-ttu-id="fd887-106">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="fd887-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="fd887-107">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="fd887-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="fd887-108">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉中會說明這些位。</span><span class="sxs-lookup"><span data-stu-id="fd887-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd887-109">備註</span><span class="sxs-lookup"><span data-stu-id="fd887-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd887-110">您應呼叫 [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) 方法，而不是此方法。</span><span class="sxs-lookup"><span data-stu-id="fd887-110">You should call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="fd887-111">雖然此 `SetEventMask` 方法會繼續受到支援，但 [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) 會提供額外的功能。</span><span class="sxs-lookup"><span data-stu-id="fd887-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd887-112">需求</span><span class="sxs-lookup"><span data-stu-id="fd887-112">Requirements</span></span>  

 <span data-ttu-id="fd887-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd887-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd887-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd887-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd887-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd887-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd887-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd887-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd887-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd887-117">See also</span></span>

- [<span data-ttu-id="fd887-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fd887-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="fd887-119">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="fd887-119">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
