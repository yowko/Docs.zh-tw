---
title: "ICorProfilerFunctionEnum::GetCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.GetCount Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55fff79bc68f1e2b790cf93afbce6a9f6cfd3c51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="2df00-102">ICorProfilerFunctionEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="2df00-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="2df00-103">取得應用程式已載入的或分析工具強制載入的函式數目。</span><span class="sxs-lookup"><span data-stu-id="2df00-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df00-104">語法</span><span class="sxs-lookup"><span data-stu-id="2df00-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2df00-105">參數</span><span class="sxs-lookup"><span data-stu-id="2df00-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2df00-106">[out]已載入的函式數目。</span><span class="sxs-lookup"><span data-stu-id="2df00-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df00-107">需求</span><span class="sxs-lookup"><span data-stu-id="2df00-107">Requirements</span></span>  
 <span data-ttu-id="2df00-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2df00-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df00-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2df00-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2df00-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df00-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2df00-111">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df00-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df00-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2df00-112">See Also</span></span>  
 [<span data-ttu-id="2df00-113">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2df00-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="2df00-114">分析介面</span><span class="sxs-lookup"><span data-stu-id="2df00-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
