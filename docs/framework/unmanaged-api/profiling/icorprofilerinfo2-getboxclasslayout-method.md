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
ms.openlocfilehash: ff39a688132112e88438bc192d7c1ab61f169400
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727155"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="e7a1f-102">ICorProfilerInfo2::GetBoxClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="e7a1f-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>

<span data-ttu-id="e7a1f-103">取得當指定之實值型別在已裝箱時所在位置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e7a1f-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7a1f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7a1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7a1f-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="e7a1f-106">在類別的識別碼，描述已封裝的實值型別。</span><span class="sxs-lookup"><span data-stu-id="e7a1f-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e7a1f-107">擴展整數，這是數值型別的相對於已封裝物件識別碼指標的位移。</span><span class="sxs-lookup"><span data-stu-id="e7a1f-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7a1f-108">備註</span><span class="sxs-lookup"><span data-stu-id="e7a1f-108">Remarks</span></span>  

 <span data-ttu-id="e7a1f-109">`pBufferOffset`值是方塊內的數值型別位置。</span><span class="sxs-lookup"><span data-stu-id="e7a1f-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="e7a1f-110">套用 `pBufferOffset` 至已封裝的物件之後，就可以使用實值型別的類別配置來解讀物件的值。</span><span class="sxs-lookup"><span data-stu-id="e7a1f-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a1f-111">需求</span><span class="sxs-lookup"><span data-stu-id="e7a1f-111">Requirements</span></span>  

 <span data-ttu-id="e7a1f-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a1f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a1f-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7a1f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7a1f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7a1f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7a1f-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a1f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a1f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7a1f-116">See also</span></span>

- [<span data-ttu-id="e7a1f-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e7a1f-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e7a1f-118">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e7a1f-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
