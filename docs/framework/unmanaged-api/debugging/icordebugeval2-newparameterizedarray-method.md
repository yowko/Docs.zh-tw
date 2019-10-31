---
title: ICorDebugEval2::NewParameterizedArray 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9476bcc9706e89fd3d7e0abc14031f70a0aa0ad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084829"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="bd03c-102">ICorDebugEval2::NewParameterizedArray 方法</span><span class="sxs-lookup"><span data-stu-id="bd03c-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="bd03c-103">Allocates a new array of the specified element type and dimensions.</span><span class="sxs-lookup"><span data-stu-id="bd03c-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd03c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd03c-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd03c-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd03c-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="bd03c-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span><span class="sxs-lookup"><span data-stu-id="bd03c-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="bd03c-107">[in] The number of dimensions of the array.</span><span class="sxs-lookup"><span data-stu-id="bd03c-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="bd03c-108">In the .NET Framework version 2.0, this value must be 1.</span><span class="sxs-lookup"><span data-stu-id="bd03c-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="bd03c-109">[in] The size, in bytes, of each dimension of the array.</span><span class="sxs-lookup"><span data-stu-id="bd03c-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="bd03c-110">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="bd03c-110">[in] Optional.</span></span> <span data-ttu-id="bd03c-111">The lower bound of each dimension of the array.</span><span class="sxs-lookup"><span data-stu-id="bd03c-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="bd03c-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span><span class="sxs-lookup"><span data-stu-id="bd03c-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd03c-113">備註</span><span class="sxs-lookup"><span data-stu-id="bd03c-113">Remarks</span></span>  
 <span data-ttu-id="bd03c-114">The elements of the array may be instances of a generic type.</span><span class="sxs-lookup"><span data-stu-id="bd03c-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="bd03c-115">The array is always created in the application domain in which the thread is currently running.</span><span class="sxs-lookup"><span data-stu-id="bd03c-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="bd03c-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span><span class="sxs-lookup"><span data-stu-id="bd03c-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd03c-117">需求</span><span class="sxs-lookup"><span data-stu-id="bd03c-117">Requirements</span></span>  
 <span data-ttu-id="bd03c-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd03c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd03c-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd03c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd03c-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd03c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd03c-121">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd03c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
