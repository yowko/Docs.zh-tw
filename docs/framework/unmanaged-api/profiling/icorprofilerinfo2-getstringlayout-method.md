---
title: ICorProfilerInfo2::GetStringLayout 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 71e2bc1d60e050d817429db5bc6926b3b16c637c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431400"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="e3486-102">ICorProfilerInfo2::GetStringLayout 方法</span><span class="sxs-lookup"><span data-stu-id="e3486-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="e3486-103">取得字串物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e3486-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="e3486-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="e3486-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3486-105">語法</span><span class="sxs-lookup"><span data-stu-id="e3486-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3486-106">參數</span><span class="sxs-lookup"><span data-stu-id="e3486-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="e3486-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span><span class="sxs-lookup"><span data-stu-id="e3486-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="e3486-108">The length is stored as a `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e3486-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3486-109">This parameter returns the length of the string itself, not the length of the buffer.</span><span class="sxs-lookup"><span data-stu-id="e3486-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="e3486-110">The length of the buffer is no longer available.</span><span class="sxs-lookup"><span data-stu-id="e3486-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="e3486-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span><span class="sxs-lookup"><span data-stu-id="e3486-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="e3486-112">The length is stored as a `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e3486-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e3486-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span><span class="sxs-lookup"><span data-stu-id="e3486-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3486-114">備註</span><span class="sxs-lookup"><span data-stu-id="e3486-114">Remarks</span></span>  
 <span data-ttu-id="e3486-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span><span class="sxs-lookup"><span data-stu-id="e3486-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="e3486-116">The length of the string's buffer.</span><span class="sxs-lookup"><span data-stu-id="e3486-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="e3486-117">The length of the string itself.</span><span class="sxs-lookup"><span data-stu-id="e3486-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="e3486-118">The buffer that contains the actual string of wide characters.</span><span class="sxs-lookup"><span data-stu-id="e3486-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="e3486-119">Strings may be null-terminated.</span><span class="sxs-lookup"><span data-stu-id="e3486-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3486-120">需求</span><span class="sxs-lookup"><span data-stu-id="e3486-120">Requirements</span></span>  
 <span data-ttu-id="e3486-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3486-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3486-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3486-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3486-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3486-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3486-124">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3486-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3486-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="e3486-125">See also</span></span>

- [<span data-ttu-id="e3486-126">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e3486-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e3486-127">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e3486-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
