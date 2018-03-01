---
title: "ICorProfilerInfo::GetClassFromObject 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ffc2e72746074776caee6fa9b87563df41fcc6b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="8a714-102">ICorProfilerInfo::GetClassFromObject 方法</span><span class="sxs-lookup"><span data-stu-id="8a714-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="8a714-103">取得`ClassID`的物件，指定其`ObjectID`。</span><span class="sxs-lookup"><span data-stu-id="8a714-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a714-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a714-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a714-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a714-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="8a714-106">[in]要取得的物件識別碼`ClassID`。</span><span class="sxs-lookup"><span data-stu-id="8a714-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="8a714-107">[out]所傳回的指標`ClassID`。</span><span class="sxs-lookup"><span data-stu-id="8a714-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a714-108">備註</span><span class="sxs-lookup"><span data-stu-id="8a714-108">Remarks</span></span>  
 <span data-ttu-id="8a714-109">Null`pClassId`表示`objectId`正在卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="8a714-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a714-110">需求</span><span class="sxs-lookup"><span data-stu-id="8a714-110">Requirements</span></span>  
 <span data-ttu-id="8a714-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a714-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a714-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a714-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a714-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a714-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a714-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a714-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a714-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a714-115">See Also</span></span>  
 [<span data-ttu-id="8a714-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8a714-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
