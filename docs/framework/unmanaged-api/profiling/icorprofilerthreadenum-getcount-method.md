---
title: ICorProfilerThreadEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b02f70f22a7d35bf0fe7816a52c490f88b31217
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218429"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="40081-102">ICorProfilerThreadEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="40081-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="40081-103">取得應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="40081-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40081-104">語法</span><span class="sxs-lookup"><span data-stu-id="40081-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40081-105">參數</span><span class="sxs-lookup"><span data-stu-id="40081-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="40081-106">[out]應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="40081-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40081-107">需求</span><span class="sxs-lookup"><span data-stu-id="40081-107">Requirements</span></span>  
 <span data-ttu-id="40081-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40081-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40081-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40081-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40081-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40081-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="40081-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="40081-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="40081-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40081-112">See also</span></span>

- [<span data-ttu-id="40081-113">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="40081-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="40081-114">分析介面</span><span class="sxs-lookup"><span data-stu-id="40081-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
