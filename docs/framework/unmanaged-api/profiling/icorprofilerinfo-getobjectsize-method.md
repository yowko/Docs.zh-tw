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
ms.openlocfilehash: 4abcf9f4575b32dd125fd8a00783043900993c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724100"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="fc3dd-102">ICorProfilerInfo::GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="fc3dd-102">ICorProfilerInfo::GetObjectSize Method</span></span>

<span data-ttu-id="fc3dd-103">取得指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc3dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc3dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc3dd-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="fc3dd-106">在物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="fc3dd-107">擴展物件大小的指標（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc3dd-108">備註</span><span class="sxs-lookup"><span data-stu-id="fc3dd-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc3dd-109">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-109">This method is obsolete.</span></span> <span data-ttu-id="fc3dd-110">它會針對64位平臺上大於4GB 的物件傳回 COR_E_OVERFLOW。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="fc3dd-111">請改用  [ICorProfilerInfo4：： GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="fc3dd-112">相同類型的不同物件通常具有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="fc3dd-113">不過，某些類型（例如陣列或字串）的每個物件可能會有不同的大小。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="fc3dd-114">方法所傳回的大小 `GetObjectSize` 不包括在物件位於垃圾收集堆積之後可能出現的對齊填補。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="fc3dd-115">如果您使用 `GetObjectSize` 方法從物件移至垃圾收集堆積上的物件，請視需要手動加入對齊填補。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="fc3dd-116">在32位的 Windows 上，COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用4位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 會使用8位元組對齊。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="fc3dd-117">在64位的 Windows 上，對齊一律為8個位元組。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc3dd-118">需求</span><span class="sxs-lookup"><span data-stu-id="fc3dd-118">Requirements</span></span>  

 <span data-ttu-id="fc3dd-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc3dd-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc3dd-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc3dd-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc3dd-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc3dd-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc3dd-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc3dd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3dd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc3dd-123">See also</span></span>

- [<span data-ttu-id="fc3dd-124">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fc3dd-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
