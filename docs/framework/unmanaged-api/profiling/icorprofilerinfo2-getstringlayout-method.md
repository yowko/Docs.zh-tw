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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc94c63edb602d87a7c08a9051eb2ef760834477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791638"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="b4f51-102">ICorProfilerInfo2::GetStringLayout 方法</span><span class="sxs-lookup"><span data-stu-id="b4f51-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="b4f51-103">取得字串物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b4f51-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="b4f51-104">這個方法已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，並已取代[ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b4f51-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f51-105">語法</span><span class="sxs-lookup"><span data-stu-id="b4f51-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4f51-106">參數</span><span class="sxs-lookup"><span data-stu-id="b4f51-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="b4f51-107">[out]指標位移的位置，相對於`ObjectID`指標，儲存字串的長度。</span><span class="sxs-lookup"><span data-stu-id="b4f51-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="b4f51-108">長度會儲存為`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="b4f51-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4f51-109">此參數會傳回字串的長度，不是緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="b4f51-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="b4f51-110">緩衝區的長度已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b4f51-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="b4f51-111">[out]指標位移的位置，相對於`ObjectID`儲存的字串本身長度的指標。</span><span class="sxs-lookup"><span data-stu-id="b4f51-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="b4f51-112">長度會儲存為`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="b4f51-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="b4f51-113">[out]相對於的緩衝區位移的指標`ObjectID`儲存的寬字元字串的指標。</span><span class="sxs-lookup"><span data-stu-id="b4f51-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4f51-114">備註</span><span class="sxs-lookup"><span data-stu-id="b4f51-114">Remarks</span></span>  
 <span data-ttu-id="b4f51-115">`GetStringLayout`方法會取得位移，相對於`ObjectID`指標，下列預存的位置：</span><span class="sxs-lookup"><span data-stu-id="b4f51-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="b4f51-116">字串的緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="b4f51-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="b4f51-117">字串本身長度。</span><span class="sxs-lookup"><span data-stu-id="b4f51-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="b4f51-118">包含實際的寬字元字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b4f51-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="b4f51-119">字串可能會以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="b4f51-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4f51-120">需求</span><span class="sxs-lookup"><span data-stu-id="b4f51-120">Requirements</span></span>  
 <span data-ttu-id="b4f51-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4f51-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4f51-122">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4f51-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4f51-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4f51-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4f51-124">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4f51-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f51-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4f51-125">See also</span></span>

- [<span data-ttu-id="b4f51-126">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="b4f51-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="b4f51-127">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="b4f51-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
