---
title: "ICorProfilerObjectEnum::Skip 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 607db61b25bafed841a81e8578438f4f70d4ee03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="9d9f0-102">ICorProfilerObjectEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="9d9f0-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="9d9f0-103">將這個列舉值的資料指標從其目前位置前移，以略過指定的項目數目。</span><span class="sxs-lookup"><span data-stu-id="9d9f0-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d9f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d9f0-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d9f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d9f0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9d9f0-106">[in]要略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="9d9f0-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d9f0-107">備註</span><span class="sxs-lookup"><span data-stu-id="9d9f0-107">Remarks</span></span>  
 <span data-ttu-id="9d9f0-108">這個列舉值的資料指標的新位置是: （目前的位置） + `celt` 。</span><span class="sxs-lookup"><span data-stu-id="9d9f0-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d9f0-109">需求</span><span class="sxs-lookup"><span data-stu-id="9d9f0-109">Requirements</span></span>  
 <span data-ttu-id="9d9f0-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9f0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d9f0-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d9f0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d9f0-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d9f0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d9f0-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d9f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9f0-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="9d9f0-114">See Also</span></span>  
 [<span data-ttu-id="9d9f0-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9d9f0-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
