---
title: "ICorProfilerThreadEnum::Skip 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f492a455165f3b49994beb3220334e2932bf214c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="baaaf-102">ICorProfilerThreadEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="baaaf-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="baaaf-103">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="baaaf-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baaaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="baaaf-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="baaaf-105">參數</span><span class="sxs-lookup"><span data-stu-id="baaaf-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="baaaf-106">[in]要略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="baaaf-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baaaf-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="baaaf-107">Return Value</span></span>  
 <span data-ttu-id="baaaf-108">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="baaaf-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="baaaf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baaaf-109">HRESULT</span></span>|<span data-ttu-id="baaaf-110">描述</span><span class="sxs-lookup"><span data-stu-id="baaaf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baaaf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="baaaf-111">S_OK</span></span>|<span data-ttu-id="baaaf-112">`celt`略過項目。</span><span class="sxs-lookup"><span data-stu-id="baaaf-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="baaaf-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="baaaf-113">S_FALSE</span></span>|<span data-ttu-id="baaaf-114">少於`celt`項目已略過，表示已沒有多個項目。</span><span class="sxs-lookup"><span data-stu-id="baaaf-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baaaf-115">備註</span><span class="sxs-lookup"><span data-stu-id="baaaf-115">Remarks</span></span>  
 <span data-ttu-id="baaaf-116">這個列舉值的資料指標的新位置時 （目前的位置） + `celt`。</span><span class="sxs-lookup"><span data-stu-id="baaaf-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baaaf-117">需求</span><span class="sxs-lookup"><span data-stu-id="baaaf-117">Requirements</span></span>  
 <span data-ttu-id="baaaf-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="baaaf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baaaf-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="baaaf-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="baaaf-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="baaaf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baaaf-121">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baaaf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaaf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baaaf-122">See Also</span></span>  
 [<span data-ttu-id="baaaf-123">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="baaaf-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="baaaf-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="baaaf-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
