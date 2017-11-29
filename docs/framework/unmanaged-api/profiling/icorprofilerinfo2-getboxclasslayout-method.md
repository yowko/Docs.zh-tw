---
title: "ICorProfilerInfo2::GetBoxClassLayout 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetBoxClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c11013781a4fc8f627dac97894ff9ef02bfda51c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="92fe1-102">ICorProfilerInfo2::GetBoxClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="92fe1-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="92fe1-103">取得指定實值類型所在的位置時，它會進行 boxed 處理的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="92fe1-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92fe1-104">語法</span><span class="sxs-lookup"><span data-stu-id="92fe1-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92fe1-105">參數</span><span class="sxs-lookup"><span data-stu-id="92fe1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="92fe1-106">[in]描述為 boxed 實值型別之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="92fe1-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="92fe1-107">[out]整數，是相對於實值類型的 boxed 的物件識別碼指標的位移。</span><span class="sxs-lookup"><span data-stu-id="92fe1-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92fe1-108">備註</span><span class="sxs-lookup"><span data-stu-id="92fe1-108">Remarks</span></span>  
 <span data-ttu-id="92fe1-109">`pBufferOffset`值是在中之值型別的位置。</span><span class="sxs-lookup"><span data-stu-id="92fe1-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="92fe1-110">之後`pBufferOffset`會套用至的 boxed 物件，值類型的類別配置可以用來解譯此物件的值。</span><span class="sxs-lookup"><span data-stu-id="92fe1-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92fe1-111">需求</span><span class="sxs-lookup"><span data-stu-id="92fe1-111">Requirements</span></span>  
 <span data-ttu-id="92fe1-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92fe1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92fe1-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92fe1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92fe1-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92fe1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92fe1-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92fe1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92fe1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92fe1-116">See Also</span></span>  
 [<span data-ttu-id="92fe1-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="92fe1-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="92fe1-118">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="92fe1-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
