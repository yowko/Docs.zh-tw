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
ms.openlocfilehash: a6e483d820d183afc8ba6a68fc4635730ffd1e51
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869312"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="430fd-102">ICorProfilerInfo::IsArrayClass 方法</span><span class="sxs-lookup"><span data-stu-id="430fd-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="430fd-103">判斷指定的類別是否為數組類別。</span><span class="sxs-lookup"><span data-stu-id="430fd-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="430fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="430fd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="430fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="430fd-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="430fd-106">在要檢查之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="430fd-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="430fd-107">脫銷CorElementType 列舉值的指標，指出陣列元素的類型。</span><span class="sxs-lookup"><span data-stu-id="430fd-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="430fd-108">脫銷陣列元素的類別 ID 指標（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="430fd-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="430fd-109">脫銷整數的指標，指出陣列的順位（也就是維度的數目）。</span><span class="sxs-lookup"><span data-stu-id="430fd-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="430fd-110">備註</span><span class="sxs-lookup"><span data-stu-id="430fd-110">Remarks</span></span>  
 <span data-ttu-id="430fd-111">如果指定的類別是陣列類別，則 `IsArrayClass` 方法會針對任何非 null 的輸出參數傳回 S_OK 的 HRESULT 和值。</span><span class="sxs-lookup"><span data-stu-id="430fd-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="430fd-112">否則，它會傳回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="430fd-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="430fd-113">需求</span><span class="sxs-lookup"><span data-stu-id="430fd-113">Requirements</span></span>  
 <span data-ttu-id="430fd-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="430fd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="430fd-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="430fd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="430fd-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="430fd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="430fd-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="430fd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430fd-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="430fd-118">See also</span></span>

- [<span data-ttu-id="430fd-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="430fd-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
