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
ms.openlocfilehash: de6d46897f3d3266bf708528efd712ca7db8ea4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438834"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="e1b7b-102">ICorProfilerInfo::GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="e1b7b-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="e1b7b-103">取得指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1b7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1b7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1b7b-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e1b7b-106">在物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="e1b7b-107">脫銷物件大小的指標（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1b7b-108">備註</span><span class="sxs-lookup"><span data-stu-id="e1b7b-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e1b7b-109">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-109">This method is obsolete.</span></span> <span data-ttu-id="e1b7b-110">它會傳回64位平臺上大於4GB 之物件的 COR_E_OVERFLOW。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="e1b7b-111">請改用[ICorProfilerInfo4：： GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="e1b7b-112">相同類型的不同物件通常具有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="e1b7b-113">不過，某些類型（例如陣列或字串）可能會有不同的大小供每個物件使用。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="e1b7b-114">`GetObjectSize` 方法所傳回的大小不包含物件在垃圾收集堆積上之後可能出現的任何對齊填補。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="e1b7b-115">如果您使用 `GetObjectSize` 方法從物件向前移至垃圾收集堆積上的物件，請視需要手動新增對齊填補。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="e1b7b-116">在32位 Windows 上，COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用4位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 使用8位元組對齊。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="e1b7b-117">在64位 Windows 上，對齊一律為8個位元組。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1b7b-118">需求</span><span class="sxs-lookup"><span data-stu-id="e1b7b-118">Requirements</span></span>  
 <span data-ttu-id="e1b7b-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1b7b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1b7b-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1b7b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1b7b-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1b7b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1b7b-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1b7b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b7b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1b7b-123">See also</span></span>

- [<span data-ttu-id="e1b7b-124">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e1b7b-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
