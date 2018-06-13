---
title: ICorProfilerInfo::IsArrayClass 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f34fee19c796f65d315fcbd26d55e1d5322303a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453024"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="be2e6-102">ICorProfilerInfo::IsArrayClass 方法</span><span class="sxs-lookup"><span data-stu-id="be2e6-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="be2e6-103">判斷指定的類別是否為陣列類別。</span><span class="sxs-lookup"><span data-stu-id="be2e6-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be2e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="be2e6-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be2e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="be2e6-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="be2e6-106">[in]要檢查的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="be2e6-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="be2e6-107">[out]CorElementType 列舉，指出陣列項目類型的值的指標。</span><span class="sxs-lookup"><span data-stu-id="be2e6-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="be2e6-108">[out]陣列項目時可用的類別識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="be2e6-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="be2e6-109">[out]表示陣列的陣序 （亦即，維度數目） 的整數指標。</span><span class="sxs-lookup"><span data-stu-id="be2e6-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be2e6-110">備註</span><span class="sxs-lookup"><span data-stu-id="be2e6-110">Remarks</span></span>  
 <span data-ttu-id="be2e6-111">如果指定的類別是陣列類別，`IsArrayClass`方法會傳回 S_OK HRESULT 和任何非 null 的輸出參數的值。</span><span class="sxs-lookup"><span data-stu-id="be2e6-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="be2e6-112">否則，它會傳回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="be2e6-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be2e6-113">需求</span><span class="sxs-lookup"><span data-stu-id="be2e6-113">Requirements</span></span>  
 <span data-ttu-id="be2e6-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be2e6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be2e6-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be2e6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be2e6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be2e6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be2e6-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be2e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2e6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be2e6-118">See Also</span></span>  
 [<span data-ttu-id="be2e6-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="be2e6-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
