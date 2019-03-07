---
title: ICorDebugEval::NewArray 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1abe307e3b9fa607912f98e456a11176eb17c56
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471504"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="65cdb-102">ICorDebugEval::NewArray 方法</span><span class="sxs-lookup"><span data-stu-id="65cdb-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="65cdb-103">配置的指定項目類型和維度的新陣列。</span><span class="sxs-lookup"><span data-stu-id="65cdb-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="65cdb-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="65cdb-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="65cdb-105">使用[ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="65cdb-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65cdb-106">語法</span><span class="sxs-lookup"><span data-stu-id="65cdb-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65cdb-107">參數</span><span class="sxs-lookup"><span data-stu-id="65cdb-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="65cdb-108">[in]CorElementType 列舉，指定陣列的項目類型的值。</span><span class="sxs-lookup"><span data-stu-id="65cdb-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="65cdb-109">[in]指定項目的類別 ICorDebugClass 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="65cdb-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="65cdb-110">此值可能為 null 如果項目型別是基本型別。</span><span class="sxs-lookup"><span data-stu-id="65cdb-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="65cdb-111">[in]陣列維度的數目。</span><span class="sxs-lookup"><span data-stu-id="65cdb-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="65cdb-112">在.NET Framework 2.0 中，此值必須是 1。</span><span class="sxs-lookup"><span data-stu-id="65cdb-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="65cdb-113">[in]以位元組為單位，每個陣列維度大小。</span><span class="sxs-lookup"><span data-stu-id="65cdb-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="65cdb-114">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="65cdb-114">[in] Optional.</span></span> <span data-ttu-id="65cdb-115">陣列的每個維度的下限。</span><span class="sxs-lookup"><span data-stu-id="65cdb-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="65cdb-116">如果省略此值，則會假設每個維度下限為零。</span><span class="sxs-lookup"><span data-stu-id="65cdb-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65cdb-117">備註</span><span class="sxs-lookup"><span data-stu-id="65cdb-117">Remarks</span></span>  
 <span data-ttu-id="65cdb-118">這個陣列是一律會建立目前執行所在之執行緒的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="65cdb-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65cdb-119">需求</span><span class="sxs-lookup"><span data-stu-id="65cdb-119">Requirements</span></span>  
 <span data-ttu-id="65cdb-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65cdb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65cdb-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65cdb-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65cdb-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65cdb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65cdb-123">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="65cdb-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
