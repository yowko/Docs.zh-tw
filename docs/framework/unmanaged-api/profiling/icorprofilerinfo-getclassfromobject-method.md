---
title: "ICorProfilerInfo::GetClassFromObject 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromObject
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 706118a197677ec97672cca36f5bcf6421a1c328
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="5c604-102">ICorProfilerInfo::GetClassFromObject 方法</span><span class="sxs-lookup"><span data-stu-id="5c604-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="5c604-103">取得`ClassID`的物件，指定其`ObjectID`。</span><span class="sxs-lookup"><span data-stu-id="5c604-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c604-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c604-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c604-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c604-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="5c604-106">[in]要取得的物件識別碼`ClassID`。</span><span class="sxs-lookup"><span data-stu-id="5c604-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="5c604-107">[out]所傳回的指標`ClassID`。</span><span class="sxs-lookup"><span data-stu-id="5c604-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c604-108">備註</span><span class="sxs-lookup"><span data-stu-id="5c604-108">Remarks</span></span>  
 <span data-ttu-id="5c604-109">Null`pClassId`表示`objectId`正在卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="5c604-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c604-110">需求</span><span class="sxs-lookup"><span data-stu-id="5c604-110">Requirements</span></span>  
 <span data-ttu-id="5c604-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c604-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c604-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c604-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c604-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c604-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c604-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c604-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c604-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c604-115">See Also</span></span>  
 [<span data-ttu-id="5c604-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="5c604-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
