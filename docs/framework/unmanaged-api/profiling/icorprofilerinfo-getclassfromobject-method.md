---
title: ICorProfilerInfo::GetClassFromObject 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9031ae9b4870c182922baaa41883de4cddb469d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676675"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="d9bf1-102">ICorProfilerInfo::GetClassFromObject 方法</span><span class="sxs-lookup"><span data-stu-id="d9bf1-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="d9bf1-103">取得`ClassID`的物件，指定其`ObjectID`。</span><span class="sxs-lookup"><span data-stu-id="d9bf1-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9bf1-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9bf1-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9bf1-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9bf1-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="d9bf1-106">[in]要取得物件的識別碼`ClassID`。</span><span class="sxs-lookup"><span data-stu-id="d9bf1-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="d9bf1-107">[out]所傳回的指標`ClassID`。</span><span class="sxs-lookup"><span data-stu-id="d9bf1-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9bf1-108">備註</span><span class="sxs-lookup"><span data-stu-id="d9bf1-108">Remarks</span></span>  
 <span data-ttu-id="d9bf1-109">Null`pClassId`表示`objectId`正在卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="d9bf1-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9bf1-110">需求</span><span class="sxs-lookup"><span data-stu-id="d9bf1-110">Requirements</span></span>  
 <span data-ttu-id="d9bf1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9bf1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9bf1-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9bf1-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9bf1-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9bf1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9bf1-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9bf1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9bf1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9bf1-115">See also</span></span>
- [<span data-ttu-id="d9bf1-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="d9bf1-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
