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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2ab0d482366b037f92a55f00dd33df8a312e84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454424"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="4ffaf-102">ICorProfilerInfo2::GetStaticFieldInfo 方法</span><span class="sxs-lookup"><span data-stu-id="4ffaf-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="4ffaf-103">取得值，指出套用到指定的欄位的靜態類型。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ffaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ffaf-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ffaf-105">參數</span><span class="sxs-lookup"><span data-stu-id="4ffaf-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4ffaf-106">[in]類別定義的靜態欄位的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4ffaf-107">[in]靜態欄位中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="4ffaf-108">[out]值的指標[COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)列舉，指出指定的欄位是否為靜態的而且如果因此的靜態類型可套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ffaf-109">備註</span><span class="sxs-lookup"><span data-stu-id="4ffaf-109">Remarks</span></span>  
 <span data-ttu-id="4ffaf-110">這項資訊可以用來判斷哪一個函式，呼叫以取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="4ffaf-111">分析工具程式碼還是應該檢查以確保它確實具有位址的靜態欄位的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="4ffaf-112">靜態的常值 （也就是常數） 只會存在於中繼資料，而且沒有位址。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ffaf-113">需求</span><span class="sxs-lookup"><span data-stu-id="4ffaf-113">Requirements</span></span>  
 <span data-ttu-id="4ffaf-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ffaf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ffaf-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ffaf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ffaf-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ffaf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ffaf-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ffaf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffaf-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ffaf-118">See Also</span></span>  
 [<span data-ttu-id="4ffaf-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4ffaf-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="4ffaf-120">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="4ffaf-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
