---
title: "ICorProfilerCallback::AssemblyUnloadStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2631650b55ec440a39a3c1a2e0c911f8868fed75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="4ab32-102">ICorProfilerCallback::AssemblyUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="4ab32-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="4ab32-103">通知分析工具正在卸載組件。</span><span class="sxs-lookup"><span data-stu-id="4ab32-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab32-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ab32-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ab32-105">參數</span><span class="sxs-lookup"><span data-stu-id="4ab32-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="4ab32-106">[in]識別正在卸載組件。</span><span class="sxs-lookup"><span data-stu-id="4ab32-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ab32-107">備註</span><span class="sxs-lookup"><span data-stu-id="4ab32-107">Remarks</span></span>  
 <span data-ttu-id="4ab32-108">值`assemblyId`不正確資訊要求之後`AssemblyUnloadStarted`方法會傳回-這是程式碼剖析工具來取得這個組件的相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="4ab32-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab32-109">需求</span><span class="sxs-lookup"><span data-stu-id="4ab32-109">Requirements</span></span>  
 <span data-ttu-id="4ab32-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ab32-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab32-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ab32-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ab32-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ab32-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ab32-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab32-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab32-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ab32-114">See Also</span></span>  
 [<span data-ttu-id="4ab32-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4ab32-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4ab32-116">AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="4ab32-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
