---
title: "ICorProfilerThreadEnum::GetCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.GetCount
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afbcb71fdaf48d07103d6ca2db48b46095dc3acd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="726a2-102">ICorProfilerThreadEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="726a2-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="726a2-103">取得應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="726a2-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="726a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="726a2-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="726a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="726a2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="726a2-106">[out]應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="726a2-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="726a2-107">需求</span><span class="sxs-lookup"><span data-stu-id="726a2-107">Requirements</span></span>  
 <span data-ttu-id="726a2-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="726a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="726a2-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="726a2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="726a2-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="726a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="726a2-111">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="726a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="726a2-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="726a2-112">See Also</span></span>  
 [<span data-ttu-id="726a2-113">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="726a2-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="726a2-114">分析介面</span><span class="sxs-lookup"><span data-stu-id="726a2-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
