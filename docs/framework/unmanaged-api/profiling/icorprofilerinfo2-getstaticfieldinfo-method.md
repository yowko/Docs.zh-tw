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
ms.openlocfilehash: c0106b2dd1151e302c0082b306d999ab5a1c4322
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177745"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="cd9e0-102">ICorProfilerInfo2::GetStaticFieldInfo 方法</span><span class="sxs-lookup"><span data-stu-id="cd9e0-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="cd9e0-103">取得值，指出套用至指定之欄位的靜態類型。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd9e0-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd9e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd9e0-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="cd9e0-106">[in]在其中定義的靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="cd9e0-107">[in]靜態欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="cd9e0-108">[out]值的指標[COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)列舉，指出是否指定的欄位是靜態的而如果等的靜態類型，套用到欄位。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd9e0-109">備註</span><span class="sxs-lookup"><span data-stu-id="cd9e0-109">Remarks</span></span>  
 <span data-ttu-id="cd9e0-110">這項資訊可用來判斷哪一個函式，呼叫以取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="cd9e0-111">分析工具程式碼仍應該檢查以確定它實際上具有位址的靜態欄位的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="cd9e0-112">靜態常值 （也就是常數） 只會存在於中繼資料，而且沒有位址。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9e0-113">需求</span><span class="sxs-lookup"><span data-stu-id="cd9e0-113">Requirements</span></span>  
 <span data-ttu-id="cd9e0-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd9e0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9e0-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd9e0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd9e0-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd9e0-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cd9e0-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="cd9e0-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd9e0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd9e0-118">See also</span></span>

- [<span data-ttu-id="cd9e0-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="cd9e0-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="cd9e0-120">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="cd9e0-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
