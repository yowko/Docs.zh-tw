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
ms.openlocfilehash: a5573765486112a83f5ea7cc9258447692f72166
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864061"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="a1ec0-102">ICorProfilerInfo::GetClassFromObject 方法</span><span class="sxs-lookup"><span data-stu-id="a1ec0-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="a1ec0-103">取得物件的 `ClassID`，指定其 `ObjectID`。</span><span class="sxs-lookup"><span data-stu-id="a1ec0-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ec0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1ec0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ec0-105">參數</span><span class="sxs-lookup"><span data-stu-id="a1ec0-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a1ec0-106">在要取得 `ClassID`之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a1ec0-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="a1ec0-107">脫銷傳回之 `ClassID`的指標。</span><span class="sxs-lookup"><span data-stu-id="a1ec0-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1ec0-108">備註</span><span class="sxs-lookup"><span data-stu-id="a1ec0-108">Remarks</span></span>  
 <span data-ttu-id="a1ec0-109">Null `pClassId` 表示 `objectId` 具有正在卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="a1ec0-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ec0-110">需求</span><span class="sxs-lookup"><span data-stu-id="a1ec0-110">Requirements</span></span>  
 <span data-ttu-id="a1ec0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1ec0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ec0-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1ec0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1ec0-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1ec0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1ec0-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ec0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ec0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1ec0-115">See also</span></span>

- [<span data-ttu-id="a1ec0-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="a1ec0-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
