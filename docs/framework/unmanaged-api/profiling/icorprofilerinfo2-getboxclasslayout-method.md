---
title: ICorProfilerInfo2::GetBoxClassLayout 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 630b67a64716f26577bbc376970e4f76216f4da5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497346"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="4e037-102">ICorProfilerInfo2::GetBoxClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="4e037-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="4e037-103">取得當指定的實值型別已被裝箱時，其所在位置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e037-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e037-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e037-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e037-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e037-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4e037-106">在類別的識別碼，描述已裝箱的實值型別。</span><span class="sxs-lookup"><span data-stu-id="4e037-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="4e037-107">脫銷整數，其為相對於實數值型別之已裝箱物件識別碼指標的位移。</span><span class="sxs-lookup"><span data-stu-id="4e037-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e037-108">備註</span><span class="sxs-lookup"><span data-stu-id="4e037-108">Remarks</span></span>  
 <span data-ttu-id="4e037-109">`pBufferOffset`值是方塊內實數值型別的位置。</span><span class="sxs-lookup"><span data-stu-id="4e037-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="4e037-110">`pBufferOffset`將套用至已裝箱的物件之後，實數值型別的類別配置就可以用來解讀物件的值。</span><span class="sxs-lookup"><span data-stu-id="4e037-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e037-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="4e037-111">Requirements</span></span>  
 <span data-ttu-id="4e037-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e037-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e037-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e037-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e037-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e037-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e037-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e037-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e037-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e037-116">See also</span></span>

- [<span data-ttu-id="4e037-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4e037-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4e037-118">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="4e037-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
