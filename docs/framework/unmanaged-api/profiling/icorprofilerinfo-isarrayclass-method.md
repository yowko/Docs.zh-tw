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
ms.openlocfilehash: 2608f91a7c5baa935e48fbe58ad4d14aaaad1f0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722501"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="6a30b-102">ICorProfilerInfo::IsArrayClass 方法</span><span class="sxs-lookup"><span data-stu-id="6a30b-102">ICorProfilerInfo::IsArrayClass Method</span></span>

<span data-ttu-id="6a30b-103">判斷指定的類別是否為數組類別。</span><span class="sxs-lookup"><span data-stu-id="6a30b-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a30b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a30b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a30b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a30b-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="6a30b-106">在要檢查之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6a30b-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="6a30b-107">擴展CorElementType 列舉值的指標，指出陣列元素的類型。</span><span class="sxs-lookup"><span data-stu-id="6a30b-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="6a30b-108">擴展陣列元素之類別識別碼的指標（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="6a30b-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="6a30b-109">擴展整數的指標，指出順位 (也就是陣列) 的維度數目。</span><span class="sxs-lookup"><span data-stu-id="6a30b-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a30b-110">備註</span><span class="sxs-lookup"><span data-stu-id="6a30b-110">Remarks</span></span>  

 <span data-ttu-id="6a30b-111">如果指定的類別是陣列類別，則方法會傳回 `IsArrayClass` S_OK 的 HRESULT，以及任何非 null 輸出參數的值。</span><span class="sxs-lookup"><span data-stu-id="6a30b-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="6a30b-112">否則，它會傳回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="6a30b-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a30b-113">需求</span><span class="sxs-lookup"><span data-stu-id="6a30b-113">Requirements</span></span>  

 <span data-ttu-id="6a30b-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a30b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a30b-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a30b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a30b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a30b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a30b-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a30b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a30b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a30b-118">See also</span></span>

- [<span data-ttu-id="6a30b-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6a30b-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
