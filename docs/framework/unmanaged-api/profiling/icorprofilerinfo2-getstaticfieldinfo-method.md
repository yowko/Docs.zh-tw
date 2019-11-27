---
title: ICorProfilerInfo2::GetStaticFieldInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: e74bab058adda759db1fb549022608eedfef5d80
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432982"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="70752-102">ICorProfilerInfo2::GetStaticFieldInfo 方法</span><span class="sxs-lookup"><span data-stu-id="70752-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="70752-103">取得值，指出套用至指定欄位的靜態類型。</span><span class="sxs-lookup"><span data-stu-id="70752-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70752-104">語法</span><span class="sxs-lookup"><span data-stu-id="70752-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70752-105">參數</span><span class="sxs-lookup"><span data-stu-id="70752-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="70752-106">在定義靜態欄位之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="70752-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="70752-107">在靜態欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="70752-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="70752-108">脫銷[COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)列舉值的指標，指出指定的欄位是否為靜態，如果是，則套用至欄位的靜態類型。</span><span class="sxs-lookup"><span data-stu-id="70752-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70752-109">備註</span><span class="sxs-lookup"><span data-stu-id="70752-109">Remarks</span></span>  
 <span data-ttu-id="70752-110">這項資訊可以用來判斷要呼叫哪個函式，以取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="70752-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="70752-111">分析工具程式碼仍應檢查靜態欄位的中繼資料，以確保它實際上有位址。</span><span class="sxs-lookup"><span data-stu-id="70752-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="70752-112">靜態常值（也就是常數）只存在於中繼資料中，而且沒有位址。</span><span class="sxs-lookup"><span data-stu-id="70752-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70752-113">需求</span><span class="sxs-lookup"><span data-stu-id="70752-113">Requirements</span></span>  
 <span data-ttu-id="70752-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70752-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70752-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70752-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70752-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70752-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70752-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70752-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70752-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="70752-118">See also</span></span>

- [<span data-ttu-id="70752-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="70752-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="70752-120">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="70752-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
