---
title: ICorProfilerInfo::GetObjectSize 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d366a0093ca82d2e5b3c40729777a1b6c0766bda
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092197"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="4a3f6-102">ICorProfilerInfo::GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="4a3f6-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="4a3f6-103">取得指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a3f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a3f6-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a3f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a3f6-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="4a3f6-106">[in]物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="4a3f6-107">[out]物件的大小，以位元組為單位的指標。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a3f6-108">備註</span><span class="sxs-lookup"><span data-stu-id="4a3f6-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a3f6-109">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-109">This method is obsolete.</span></span> <span data-ttu-id="4a3f6-110">它會傳回 COR_E_OVERFLOW 物件大於 4 GB 64 位元平台上。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="4a3f6-111">使用[ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="4a3f6-112">不同的物件相同的類型通常會有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="4a3f6-113">不過，某些類型，例如陣列或字串，可能會有不同的大小，為每個物件。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="4a3f6-114">所傳回的大小`GetObjectSize`方法不包含在記憶體回收堆積上物件之後，可能會出現任何對齊填補。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="4a3f6-115">如果您使用`GetObjectSize`方法前進 object 物件在記憶體回收堆積，新增以手動方式，視需要填補的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="4a3f6-116">在 32 位元 Windows COR_PRF_GC_GEN_0、 COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用 4 位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 會使用 8 位元組對齊。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="4a3f6-117">在 64 位元 Windows 上的對齊方式一定是 8 個位元組。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a3f6-118">需求</span><span class="sxs-lookup"><span data-stu-id="4a3f6-118">Requirements</span></span>  
 <span data-ttu-id="4a3f6-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a3f6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a3f6-120">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a3f6-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a3f6-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a3f6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a3f6-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a3f6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3f6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a3f6-123">See also</span></span>

- [<span data-ttu-id="4a3f6-124">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4a3f6-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
