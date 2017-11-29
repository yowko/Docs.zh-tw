---
title: "ICorProfilerInfo::IsArrayClass 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.IsArrayClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cd07541095158d17b80333b83015d6b1f33a5dcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="128c0-102">ICorProfilerInfo::IsArrayClass 方法</span><span class="sxs-lookup"><span data-stu-id="128c0-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="128c0-103">判斷指定的類別是否為陣列類別。</span><span class="sxs-lookup"><span data-stu-id="128c0-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="128c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="128c0-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="128c0-105">參數</span><span class="sxs-lookup"><span data-stu-id="128c0-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="128c0-106">[in]要檢查的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="128c0-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="128c0-107">[out]CorElementType 列舉，指出陣列項目類型的值的指標。</span><span class="sxs-lookup"><span data-stu-id="128c0-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="128c0-108">[out]陣列項目時可用的類別識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="128c0-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="128c0-109">[out]表示陣列的陣序 （亦即，維度數目） 的整數指標。</span><span class="sxs-lookup"><span data-stu-id="128c0-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="128c0-110">備註</span><span class="sxs-lookup"><span data-stu-id="128c0-110">Remarks</span></span>  
 <span data-ttu-id="128c0-111">如果指定的類別是陣列類別，`IsArrayClass`方法會傳回 S_OK HRESULT 和任何非 null 的輸出參數的值。</span><span class="sxs-lookup"><span data-stu-id="128c0-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="128c0-112">否則，它會傳回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="128c0-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="128c0-113">需求</span><span class="sxs-lookup"><span data-stu-id="128c0-113">Requirements</span></span>  
 <span data-ttu-id="128c0-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="128c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="128c0-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="128c0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="128c0-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="128c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="128c0-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="128c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128c0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="128c0-118">See Also</span></span>  
 [<span data-ttu-id="128c0-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="128c0-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
