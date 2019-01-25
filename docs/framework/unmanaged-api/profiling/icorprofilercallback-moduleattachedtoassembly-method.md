---
title: ICorProfilerCallback::ModuleAttachedToAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff819ab67b258dbc7b5cec937863753852b1fcc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629315"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="515f3-102">ICorProfilerCallback::ModuleAttachedToAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="515f3-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="515f3-103">通知分析工具模組，附加到其父組件。</span><span class="sxs-lookup"><span data-stu-id="515f3-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="515f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="515f3-104">Syntax</span></span>  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="515f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="515f3-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="515f3-106">[in]要附加的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="515f3-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="515f3-107">[in]要附加之模組的父組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="515f3-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="515f3-108">備註</span><span class="sxs-lookup"><span data-stu-id="515f3-108">Remarks</span></span>  
 <span data-ttu-id="515f3-109">可以透過匯入位址表 (IAT)、 載入模組，透過呼叫`LoadLibrary`，或透過中繼資料參考。</span><span class="sxs-lookup"><span data-stu-id="515f3-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="515f3-110">如此一來，common language runtime (CLR) 載入器會有多個程式碼路徑，來判斷模組存留在其中的組件。</span><span class="sxs-lookup"><span data-stu-id="515f3-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="515f3-111">因此，很可能之後[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)呼叫時，此模組並不知道哪一個組件中，而且不可能取得父組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="515f3-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="515f3-112">`ModuleAttachedToAssembly`模組連接到其父組件，且它可以取得識別碼的父組件時，會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="515f3-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="515f3-113">需求</span><span class="sxs-lookup"><span data-stu-id="515f3-113">Requirements</span></span>  
 <span data-ttu-id="515f3-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="515f3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="515f3-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="515f3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="515f3-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="515f3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="515f3-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="515f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515f3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515f3-118">See also</span></span>
- [<span data-ttu-id="515f3-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="515f3-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
