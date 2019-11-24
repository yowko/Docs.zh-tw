---
title: ICorProfilerInfo3::GetStringLayout2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: 1e3dc4735af68da7f76fc6fce84d2dd4ac3f576e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449661"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="ab878-102">ICorProfilerInfo3::GetStringLayout2 方法</span><span class="sxs-lookup"><span data-stu-id="ab878-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="ab878-103">取得字串物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ab878-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="ab878-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="ab878-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab878-105">語法</span><span class="sxs-lookup"><span data-stu-id="ab878-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab878-106">參數</span><span class="sxs-lookup"><span data-stu-id="ab878-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="ab878-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span><span class="sxs-lookup"><span data-stu-id="ab878-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="ab878-108">The length is stored as a `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="ab878-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="ab878-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span><span class="sxs-lookup"><span data-stu-id="ab878-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab878-110">備註</span><span class="sxs-lookup"><span data-stu-id="ab878-110">Remarks</span></span>  
 <span data-ttu-id="ab878-111">Strings may or may not be null-terminated.</span><span class="sxs-lookup"><span data-stu-id="ab878-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab878-112">需求</span><span class="sxs-lookup"><span data-stu-id="ab878-112">Requirements</span></span>  
 <span data-ttu-id="ab878-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab878-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab878-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab878-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab878-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab878-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab878-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab878-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab878-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab878-117">See also</span></span>

- [<span data-ttu-id="ab878-118">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="ab878-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ab878-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="ab878-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
