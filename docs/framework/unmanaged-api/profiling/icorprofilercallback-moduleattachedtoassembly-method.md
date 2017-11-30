---
title: "ICorProfilerCallback::ModuleAttachedToAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c285a42bb48970756a54d5313d2839c76a9835c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="e1122-102">ICorProfilerCallback::ModuleAttachedToAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="e1122-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="e1122-103">通知分析工具模組要附加到其父組件。</span><span class="sxs-lookup"><span data-stu-id="e1122-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1122-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1122-104">Syntax</span></span>  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1122-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1122-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="e1122-106">[in]要附加的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="e1122-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="e1122-107">[in]要附加之模組的父組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="e1122-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1122-108">備註</span><span class="sxs-lookup"><span data-stu-id="e1122-108">Remarks</span></span>  
 <span data-ttu-id="e1122-109">可以透過匯入位址表 (IAT)，載入模組，透過呼叫`LoadLibrary`，或透過中繼資料參考。</span><span class="sxs-lookup"><span data-stu-id="e1122-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="e1122-110">如此一來，common language runtime (CLR) 載入器有多個程式碼路徑，以判斷模組存在所在的組件。</span><span class="sxs-lookup"><span data-stu-id="e1122-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="e1122-111">因此，可能會之後[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)呼叫時，此模組並不知道哪一個組件處於和取得父組件識別碼不可行。</span><span class="sxs-lookup"><span data-stu-id="e1122-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="e1122-112">`ModuleAttachedToAssembly`模組附加至其父組件和識別碼可透過其父組件時，呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e1122-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1122-113">需求</span><span class="sxs-lookup"><span data-stu-id="e1122-113">Requirements</span></span>  
 <span data-ttu-id="e1122-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1122-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1122-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1122-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1122-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1122-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1122-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1122-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1122-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1122-118">See Also</span></span>  
 [<span data-ttu-id="e1122-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e1122-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
