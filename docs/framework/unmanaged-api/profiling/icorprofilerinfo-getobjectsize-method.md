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
ms.openlocfilehash: 8d395d498dd34cb0cbc93e898761c87dcd5ec42a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="084c4-102">ICorProfilerInfo::GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="084c4-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="084c4-103">取得指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="084c4-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="084c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="084c4-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="084c4-105">參數</span><span class="sxs-lookup"><span data-stu-id="084c4-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="084c4-106">[in]物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="084c4-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="084c4-107">[out]物件的大小 （位元組） 指標。</span><span class="sxs-lookup"><span data-stu-id="084c4-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="084c4-108">備註</span><span class="sxs-lookup"><span data-stu-id="084c4-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="084c4-109">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="084c4-109">This method is obsolete.</span></span> <span data-ttu-id="084c4-110">它會傳回 COR_E_OVERFLOW 物件大於 4 GB 在 64 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="084c4-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="084c4-111">使用[icorprofilerinfo4:: Getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="084c4-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="084c4-112">相同的類型不同的物件通常會有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="084c4-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="084c4-113">不過，某些類型，例如陣列或字串，可能必須針對每個物件的大小不同。</span><span class="sxs-lookup"><span data-stu-id="084c4-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="084c4-114">所傳回的大小`GetObjectSize`方法不包含在記憶體回收堆積上物件之後，可能會出現任何對齊填補。</span><span class="sxs-lookup"><span data-stu-id="084c4-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="084c4-115">如果您使用`GetObjectSize`前進物件物件在記憶體回收堆積，方法中加入手動視需要填補的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="084c4-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="084c4-116">32 位元 Windows 上 COR_PRF_GC_GEN_0、 COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用 4 位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 使用 8 位元組對齊。</span><span class="sxs-lookup"><span data-stu-id="084c4-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="084c4-117">在 64 位元 Windows 上對齊一定是 8 個位元組。</span><span class="sxs-lookup"><span data-stu-id="084c4-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="084c4-118">需求</span><span class="sxs-lookup"><span data-stu-id="084c4-118">Requirements</span></span>  
 <span data-ttu-id="084c4-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="084c4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="084c4-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="084c4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="084c4-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="084c4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="084c4-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="084c4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084c4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="084c4-123">See Also</span></span>  
 [<span data-ttu-id="084c4-124">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="084c4-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
