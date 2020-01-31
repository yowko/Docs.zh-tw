---
title: ICorDebugType::EnumerateTypeParameters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791304"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="8f2c6-102">ICorDebugType::EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="8f2c6-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="8f2c6-103">取得 ICorDebugTypeEnum 的介面指標，其中包含這個 ICorDebugType 所參考之類別的 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f2c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f2c6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f2c6-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f2c6-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="8f2c6-106">脫銷包含型別參數之 `ICorDebugTypeEnum` 位址的指標。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f2c6-107">備註</span><span class="sxs-lookup"><span data-stu-id="8f2c6-107">Remarks</span></span>  
 <span data-ttu-id="8f2c6-108">如果[ICorDebugType：： GetType](icordebugtype-gettype-method.md)傳回的 CorElementType 值是 ELEMENT_TYPE_CLASS、ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_FNPTR，您可以使用 `EnumerateTypeParameters`。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="8f2c6-109">參數和其順序的數目取決於類型：</span><span class="sxs-lookup"><span data-stu-id="8f2c6-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="8f2c6-110">ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE：這個方法傳回的 `ICorDebugTypeEnum` 中包含的類型參數數目，將取決於對應類別的型式類型參數數目。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="8f2c6-111">例如，如果類型是 `class Dict<String,int32>`，則 `EnumerateTypeParameters` 會傳回 `ICorDebugTypeEnum`，其中包含以序清單示 `String` 和 `int32` 的物件。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="8f2c6-112">ELEMENT_TYPE_FNPTR： `ICorDebugTypeEnum` 中包含的型別參數數目會大於函數接受的引數數目。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="8f2c6-113">`ICorDebugTypeEnum` 中所包含的第一個型別參數是函式的傳回型別，而後續的型別參數則是函數的參數。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="8f2c6-114">ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR：將會傳回一個型別參數。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="8f2c6-115">例如，如果型別是陣列型別，例如 `int32[]`，`EnumerateTypeParameters` 會傳回一個 `ICorDebugTypeEnum`，其中包含代表 `int32`的物件。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f2c6-116">需求</span><span class="sxs-lookup"><span data-stu-id="8f2c6-116">Requirements</span></span>  
 <span data-ttu-id="8f2c6-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f2c6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f2c6-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f2c6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f2c6-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f2c6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f2c6-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f2c6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
