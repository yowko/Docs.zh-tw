---
title: "ICorProfilerInfo::GetObjectSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetObjectSize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9425938042485c4330fe3fbc50cdabde6451b427
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="c2969-102">ICorProfilerInfo::GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="c2969-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="c2969-103">取得指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="c2969-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2969-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2969-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2969-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2969-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="c2969-106">[in]物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c2969-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="c2969-107">[out]物件的大小 （位元組） 指標。</span><span class="sxs-lookup"><span data-stu-id="c2969-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2969-108">備註</span><span class="sxs-lookup"><span data-stu-id="c2969-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2969-109">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="c2969-109">This method is obsolete.</span></span> <span data-ttu-id="c2969-110">它會傳回 COR_E_OVERFLOW 物件大於 4 GB 在 64 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="c2969-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="c2969-111">使用[icorprofilerinfo4:: Getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="c2969-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="c2969-112">相同的類型不同的物件通常會有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="c2969-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="c2969-113">不過，某些類型，例如陣列或字串，可能必須針對每個物件的大小不同。</span><span class="sxs-lookup"><span data-stu-id="c2969-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="c2969-114">所傳回的大小`GetObjectSize`方法不包含在記憶體回收堆積上物件之後，可能會出現任何對齊填補。</span><span class="sxs-lookup"><span data-stu-id="c2969-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="c2969-115">如果您使用`GetObjectSize`前進物件物件在記憶體回收堆積，方法中加入手動視需要填補的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="c2969-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="c2969-116">32 位元 Windows 上 COR_PRF_GC_GEN_0、 COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用 4 位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 使用 8 位元組對齊。</span><span class="sxs-lookup"><span data-stu-id="c2969-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="c2969-117">在 64 位元 Windows 上對齊一定是 8 個位元組。</span><span class="sxs-lookup"><span data-stu-id="c2969-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2969-118">需求</span><span class="sxs-lookup"><span data-stu-id="c2969-118">Requirements</span></span>  
 <span data-ttu-id="c2969-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2969-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2969-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2969-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2969-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2969-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2969-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2969-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2969-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2969-123">See Also</span></span>  
 [<span data-ttu-id="c2969-124">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c2969-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
