---
title: ICorProfilerCallback::JITInlining 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53a8f9aefa4460493113c035aa05e971b05d5167
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500167"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="7d341-102">ICorProfilerCallback::JITInlining 方法</span><span class="sxs-lookup"><span data-stu-id="7d341-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="7d341-103">通知分析工具，在 just-in-time (JIT) 編譯器插入符合另一個函式的函式。</span><span class="sxs-lookup"><span data-stu-id="7d341-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d341-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d341-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d341-105">參數</span><span class="sxs-lookup"><span data-stu-id="7d341-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="7d341-106">[in]在其中函式的識別碼`calleeId`函式會插入。</span><span class="sxs-lookup"><span data-stu-id="7d341-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="7d341-107">[in]要插入函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7d341-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="7d341-108">[out]`true`允許發生; 插入，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="7d341-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d341-109">備註</span><span class="sxs-lookup"><span data-stu-id="7d341-109">Remarks</span></span>  
 <span data-ttu-id="7d341-110">分析工具可以設定`pfShouldInline`要`false`若要避免`calleeId`函式插入`callerId`函式。</span><span class="sxs-lookup"><span data-stu-id="7d341-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="7d341-111">此外，分析工具可以全域使用停用內嵌插入 COR_PRF_DISABLE_INLINING 值[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="7d341-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="7d341-112">插入函式內嵌不會引發事件進入或離開。</span><span class="sxs-lookup"><span data-stu-id="7d341-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="7d341-113">因此，必須設定分析工具`pfShouldInline`至`false`才能產生精確的 callgraph。</span><span class="sxs-lookup"><span data-stu-id="7d341-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="7d341-114">設定`pfShouldInline`至`false`會影響效能，因為內嵌插入通常會增加速度和減少的插入方法的不同 JIT 編譯事件。</span><span class="sxs-lookup"><span data-stu-id="7d341-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d341-115">需求</span><span class="sxs-lookup"><span data-stu-id="7d341-115">Requirements</span></span>  
 <span data-ttu-id="7d341-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d341-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d341-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7d341-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d341-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d341-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d341-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d341-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d341-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d341-120">See also</span></span>
- [<span data-ttu-id="7d341-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7d341-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
