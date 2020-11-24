---
title: ICorProfilerInfo5::GetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: 81509db178b0ab1a524dcc4b00f39264e87a220d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682779"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="e69f9-102">ICorProfilerInfo5::GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="e69f9-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>

<span data-ttu-id="e69f9-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="e69f9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e69f9-104">取得分析工具想要從 Common Language Runtime (CLR) 接收通知的目前事件分類。</span><span class="sxs-lookup"><span data-stu-id="e69f9-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="e69f9-105">它提供 [ICorProfilerInfo：： GetEventMask](icorprofilerinfo-geteventmask-method.md) 方法未提供的功能。</span><span class="sxs-lookup"><span data-stu-id="e69f9-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e69f9-106">語法</span><span class="sxs-lookup"><span data-stu-id="e69f9-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e69f9-107">參數</span><span class="sxs-lookup"><span data-stu-id="e69f9-107">Parameters</span></span>  

 `pdwEventsLow`  
 <span data-ttu-id="e69f9-108">[out] 指定事件分類的 4 位元組值的指標。</span><span class="sxs-lookup"><span data-stu-id="e69f9-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="e69f9-109">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="e69f9-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="e69f9-110">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉中會說明這些位。</span><span class="sxs-lookup"><span data-stu-id="e69f9-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="e69f9-111">[out] 指定事件分類的 4 位元組值的指標。</span><span class="sxs-lookup"><span data-stu-id="e69f9-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="e69f9-112">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="e69f9-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="e69f9-113">[COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md)列舉中會說明這些位。</span><span class="sxs-lookup"><span data-stu-id="e69f9-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e69f9-114">備註</span><span class="sxs-lookup"><span data-stu-id="e69f9-114">Remarks</span></span>  

 <span data-ttu-id="e69f9-115">`GetEventMask2` 方法可用於判斷分析工具已訂閱哪些回呼。</span><span class="sxs-lookup"><span data-stu-id="e69f9-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="e69f9-116">一般來說，您會執行和值的邏輯 OR， `pdwEventsLow` `pdwEventsHigh` 以及您想要設定的任何新位，然後呼叫 [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="e69f9-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="e69f9-117">這是 [GetEventMask](icorprofilerinfo-geteventmask-method.md) 方法的建議替代方法。</span><span class="sxs-lookup"><span data-stu-id="e69f9-117">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e69f9-118">需求</span><span class="sxs-lookup"><span data-stu-id="e69f9-118">Requirements</span></span>  

 <span data-ttu-id="e69f9-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e69f9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e69f9-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e69f9-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e69f9-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e69f9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e69f9-122">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e69f9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69f9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e69f9-123">See also</span></span>

- [<span data-ttu-id="e69f9-124">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="e69f9-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="e69f9-125">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="e69f9-125">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
