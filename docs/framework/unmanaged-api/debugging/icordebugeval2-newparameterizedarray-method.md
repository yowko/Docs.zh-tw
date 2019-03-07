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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c639204fa207774b0e362f1ba8fe71937494ae2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487680"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="d5501-102">ICorDebugEval2::NewParameterizedArray 方法</span><span class="sxs-lookup"><span data-stu-id="d5501-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="d5501-103">配置的指定項目類型和維度的新陣列。</span><span class="sxs-lookup"><span data-stu-id="d5501-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5501-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5501-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5501-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5501-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="d5501-106">[in]ICorDebugType 物件，表示儲存在陣列中元素的類型指標。</span><span class="sxs-lookup"><span data-stu-id="d5501-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="d5501-107">[in]陣列維度的數目。</span><span class="sxs-lookup"><span data-stu-id="d5501-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="d5501-108">在.NET Framework 2.0 版中，此值必須是 1。</span><span class="sxs-lookup"><span data-stu-id="d5501-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="d5501-109">[in]以位元組為單位，每個陣列維度大小。</span><span class="sxs-lookup"><span data-stu-id="d5501-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="d5501-110">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="d5501-110">[in] Optional.</span></span> <span data-ttu-id="d5501-111">陣列的每個維度的下限。</span><span class="sxs-lookup"><span data-stu-id="d5501-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="d5501-112">如果省略此值，則會假設每個維度下限為零。</span><span class="sxs-lookup"><span data-stu-id="d5501-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5501-113">備註</span><span class="sxs-lookup"><span data-stu-id="d5501-113">Remarks</span></span>  
 <span data-ttu-id="d5501-114">陣列的項目可以是泛型類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d5501-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="d5501-115">這個陣列是一律會建立目前執行中執行緒的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="d5501-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="d5501-116">在.NET Framework 2.0 的值`rank`必須是 1。</span><span class="sxs-lookup"><span data-stu-id="d5501-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5501-117">需求</span><span class="sxs-lookup"><span data-stu-id="d5501-117">Requirements</span></span>  
 <span data-ttu-id="d5501-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5501-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5501-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5501-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5501-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5501-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5501-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5501-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
