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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ebbc3422f48c0c2b8ff7b807228c63fbb35dd7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454093"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="44874-102">ICorProfilerInfo4::GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="44874-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="44874-103">傳回指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="44874-103">Returns the size of a specified object.</span></span> <span data-ttu-id="44874-104">取代[icorprofilerinfo:: Getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)報告大於中能表示的物件大小的方法`ULONG`。</span><span class="sxs-lookup"><span data-stu-id="44874-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44874-105">語法</span><span class="sxs-lookup"><span data-stu-id="44874-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44874-106">參數</span><span class="sxs-lookup"><span data-stu-id="44874-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="44874-107">[in]物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="44874-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="44874-108">[out]物件的大小 （位元組） 指標。</span><span class="sxs-lookup"><span data-stu-id="44874-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44874-109">備註</span><span class="sxs-lookup"><span data-stu-id="44874-109">Remarks</span></span>  
 <span data-ttu-id="44874-110">相同的類型不同的物件通常會有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="44874-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="44874-111">不過，某些類型，例如陣列或字串，可能必須針對每個物件的大小不同。</span><span class="sxs-lookup"><span data-stu-id="44874-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44874-112">需求</span><span class="sxs-lookup"><span data-stu-id="44874-112">Requirements</span></span>  
 <span data-ttu-id="44874-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44874-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44874-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44874-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44874-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44874-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44874-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44874-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44874-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44874-117">See Also</span></span>  
 [<span data-ttu-id="44874-118">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="44874-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
