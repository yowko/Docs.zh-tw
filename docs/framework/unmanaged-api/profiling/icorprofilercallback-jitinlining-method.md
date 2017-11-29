---
title: "ICorProfilerCallback::JITInlining 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITInlining
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1e729a17101bbe9c659be729c685909932b5456
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="10a0a-102">ICorProfilerCallback::JITInlining 方法</span><span class="sxs-lookup"><span data-stu-id="10a0a-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="10a0a-103">通知分析工具在 just-in-time (JIT) 編譯器即將插入與另一個函式的函式。</span><span class="sxs-lookup"><span data-stu-id="10a0a-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10a0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="10a0a-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10a0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="10a0a-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="10a0a-106">[in]所在的函式 ID`calleeId`函式將會插入。</span><span class="sxs-lookup"><span data-stu-id="10a0a-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="10a0a-107">[in]要插入的函式 ID。</span><span class="sxs-lookup"><span data-stu-id="10a0a-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="10a0a-108">[out]`true`允許插入發生; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="10a0a-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10a0a-109">備註</span><span class="sxs-lookup"><span data-stu-id="10a0a-109">Remarks</span></span>  
 <span data-ttu-id="10a0a-110">分析工具可以設定`pfShouldInline`至`false`防止`calleeId`函式插入`callerId`函式。</span><span class="sxs-lookup"><span data-stu-id="10a0a-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="10a0a-111">此外，分析工具可以全域使用停用內嵌插入 COR_PRF_DISABLE_INLINING 值[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="10a0a-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="10a0a-112">內嵌函式插入不會引發事件進入或離開。</span><span class="sxs-lookup"><span data-stu-id="10a0a-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="10a0a-113">因此，必須設定程式碼剖析工具`pfShouldInline`至`false`才能產生精確範圍的 callgraph。</span><span class="sxs-lookup"><span data-stu-id="10a0a-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="10a0a-114">設定`pfShouldInline`至`false`會影響效能，因為內嵌插入通常會提升速度和減少插入的方法不同的 JIT 編譯事件。</span><span class="sxs-lookup"><span data-stu-id="10a0a-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10a0a-115">需求</span><span class="sxs-lookup"><span data-stu-id="10a0a-115">Requirements</span></span>  
 <span data-ttu-id="10a0a-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10a0a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10a0a-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10a0a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10a0a-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10a0a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10a0a-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10a0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a0a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10a0a-120">See Also</span></span>  
 [<span data-ttu-id="10a0a-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="10a0a-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
