---
title: "ICorDebugEval2::NewParameterizedArray 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a605276fac66e395d5663bacff727c235981a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="71d5d-102">ICorDebugEval2::NewParameterizedArray 方法</span><span class="sxs-lookup"><span data-stu-id="71d5d-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="71d5d-103">配置的指定項目類型和維度的新陣列。</span><span class="sxs-lookup"><span data-stu-id="71d5d-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="71d5d-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71d5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="71d5d-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="71d5d-106">[in]ICorDebugType 物件代表儲存在陣列中的項目類型的指標。</span><span class="sxs-lookup"><span data-stu-id="71d5d-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="71d5d-107">[in]陣列維度的數目。</span><span class="sxs-lookup"><span data-stu-id="71d5d-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="71d5d-108">在.NET Framework 2.0 版中，這個值必須是 1。</span><span class="sxs-lookup"><span data-stu-id="71d5d-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="71d5d-109">[in]單位為位元組陣列的每個維度大小。</span><span class="sxs-lookup"><span data-stu-id="71d5d-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="71d5d-110">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="71d5d-110">[in] Optional.</span></span> <span data-ttu-id="71d5d-111">陣列的每個維度的下限。</span><span class="sxs-lookup"><span data-stu-id="71d5d-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="71d5d-112">如果省略此值，則會假設每個維度下限為零。</span><span class="sxs-lookup"><span data-stu-id="71d5d-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71d5d-113">備註</span><span class="sxs-lookup"><span data-stu-id="71d5d-113">Remarks</span></span>  
 <span data-ttu-id="71d5d-114">陣列的項目可能是泛型類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="71d5d-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="71d5d-115">陣列一律是目前執行中執行緒的應用程式定義域中建立的。</span><span class="sxs-lookup"><span data-stu-id="71d5d-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="71d5d-116">在.NET Framework 2.0 中，值`rank`必須是 1。</span><span class="sxs-lookup"><span data-stu-id="71d5d-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d5d-117">需求</span><span class="sxs-lookup"><span data-stu-id="71d5d-117">Requirements</span></span>  
 <span data-ttu-id="71d5d-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71d5d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d5d-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71d5d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71d5d-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71d5d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71d5d-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71d5d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
