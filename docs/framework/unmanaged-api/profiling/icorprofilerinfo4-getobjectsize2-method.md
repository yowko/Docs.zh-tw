---
title: ICorProfilerInfo4::GetObjectSize2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 441f7743ba01884592393ce9382348fbecaeaa9d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861875"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="470e1-102">ICorProfilerInfo4::GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="470e1-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="470e1-103">傳回指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="470e1-103">Returns the size of a specified object.</span></span> <span data-ttu-id="470e1-104">藉由報告大於 `ULONG`中可表示之物件的大小，來取代[ICorProfilerInfo：： GetObjectSize](icorprofilerinfo-getobjectsize-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="470e1-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="470e1-105">語法</span><span class="sxs-lookup"><span data-stu-id="470e1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="470e1-106">參數</span><span class="sxs-lookup"><span data-stu-id="470e1-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="470e1-107">在物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="470e1-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="470e1-108">脫銷物件大小的指標（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="470e1-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="470e1-109">備註</span><span class="sxs-lookup"><span data-stu-id="470e1-109">Remarks</span></span>  
 <span data-ttu-id="470e1-110">相同類型的不同物件通常具有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="470e1-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="470e1-111">不過，某些類型（例如陣列或字串）可能會有不同的大小供每個物件使用。</span><span class="sxs-lookup"><span data-stu-id="470e1-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="470e1-112">需求</span><span class="sxs-lookup"><span data-stu-id="470e1-112">Requirements</span></span>  
 <span data-ttu-id="470e1-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="470e1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="470e1-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="470e1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="470e1-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="470e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="470e1-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="470e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="470e1-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="470e1-117">See also</span></span>

- [<span data-ttu-id="470e1-118">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="470e1-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
