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
ms.openlocfilehash: 4f494919d11e0f979cf1964c08106fbb9b9ed20b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503389"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="141a0-102">ICorProfilerCallback::ModuleAttachedToAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="141a0-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="141a0-103">通知 profiler，模組已附加至其父元件。</span><span class="sxs-lookup"><span data-stu-id="141a0-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="141a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="141a0-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="141a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="141a0-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="141a0-106">在所附加之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="141a0-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="141a0-107">在模組所附加之父元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="141a0-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="141a0-108">備註</span><span class="sxs-lookup"><span data-stu-id="141a0-108">Remarks</span></span>  
 <span data-ttu-id="141a0-109">模組可以透過匯入位址表（IAT）、透過呼叫 `LoadLibrary` ，或透過中繼資料參考來載入。</span><span class="sxs-lookup"><span data-stu-id="141a0-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="141a0-110">因此，common language runtime （CLR）載入器有多個程式碼路徑可用於判斷模組所在的元件。</span><span class="sxs-lookup"><span data-stu-id="141a0-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="141a0-111">因此，在呼叫[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)之後，模組不知道它所在的元件，而且無法取得父元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="141a0-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="141a0-112">`ModuleAttachedToAssembly`當模組附加至其父元件，而且可以取得其父元件識別碼時，會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="141a0-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="141a0-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="141a0-113">Requirements</span></span>  
 <span data-ttu-id="141a0-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="141a0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="141a0-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="141a0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="141a0-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="141a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="141a0-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="141a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141a0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="141a0-118">See also</span></span>

- [<span data-ttu-id="141a0-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="141a0-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
