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
ms.openlocfilehash: 9d589bfc3093d03d87acb47ade0fc6c972bcd335
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976105"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="2a811-102">ICorDebugEval2::NewParameterizedArray 方法</span><span class="sxs-lookup"><span data-stu-id="2a811-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="2a811-103">配置指定之元素類型和維度的新陣列。</span><span class="sxs-lookup"><span data-stu-id="2a811-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a811-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a811-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a811-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a811-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="2a811-106">在ICorDebugType 物件的指標，代表儲存在陣列中的元素類型。</span><span class="sxs-lookup"><span data-stu-id="2a811-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="2a811-107">在陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="2a811-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="2a811-108">在 .NET Framework 版本2.0 中，此值必須是1。</span><span class="sxs-lookup"><span data-stu-id="2a811-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="2a811-109">在陣列的每個維度大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2a811-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="2a811-110">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="2a811-110">[in] Optional.</span></span> <span data-ttu-id="2a811-111">陣列的每個維度下限。</span><span class="sxs-lookup"><span data-stu-id="2a811-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="2a811-112">如果省略此值，則會假設每個維度的下限為零。</span><span class="sxs-lookup"><span data-stu-id="2a811-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a811-113">備註</span><span class="sxs-lookup"><span data-stu-id="2a811-113">Remarks</span></span>  
 <span data-ttu-id="2a811-114">陣列的元素可以是泛型型別的實例。</span><span class="sxs-lookup"><span data-stu-id="2a811-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="2a811-115">陣列一律會建立線上程目前執行所在的應用程式域中。</span><span class="sxs-lookup"><span data-stu-id="2a811-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="2a811-116">在 .NET Framework 2.0 中，的值`rank`必須是1。</span><span class="sxs-lookup"><span data-stu-id="2a811-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a811-117">需求</span><span class="sxs-lookup"><span data-stu-id="2a811-117">Requirements</span></span>  
 <span data-ttu-id="2a811-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a811-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a811-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a811-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a811-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a811-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a811-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a811-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
