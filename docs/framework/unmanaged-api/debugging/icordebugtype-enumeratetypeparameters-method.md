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
ms.openlocfilehash: 3717497ab6e72f0ce67f688813ee7264206e8c84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727948"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="759e6-102">ICorDebugType::EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="759e6-102">ICorDebugType::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="759e6-103">取得 ICorDebugTypeEnum 的介面指標，其中包含 <xref:System.Type> 這個 ICorDebugType 所參考之類別的參數。</span><span class="sxs-lookup"><span data-stu-id="759e6-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="759e6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="759e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="759e6-105">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="759e6-106">擴展的位址指標 `ICorDebugTypeEnum` ，其中包含類型的參數。</span><span class="sxs-lookup"><span data-stu-id="759e6-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="759e6-107">備註</span><span class="sxs-lookup"><span data-stu-id="759e6-107">Remarks</span></span>  

 <span data-ttu-id="759e6-108">您可以使用， `EnumerateTypeParameters` 如果 [ICorDebugType：： GetType](icordebugtype-gettype-method.md) 傳回的 CorElementType 值為 ELEMENT_TYPE_CLASS、ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_FNPTR。</span><span class="sxs-lookup"><span data-stu-id="759e6-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="759e6-109">參數的數目及其順序取決於類型：</span><span class="sxs-lookup"><span data-stu-id="759e6-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="759e6-110">ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE：這個方法所傳回之的型別參數數目 `ICorDebugTypeEnum` ，將取決於對應類別的正式型別參數數目。</span><span class="sxs-lookup"><span data-stu-id="759e6-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="759e6-111">例如，如果類型為 `class Dict<String,int32>` ，則會傳回， `EnumerateTypeParameters` `ICorDebugTypeEnum` 其中包含代表 `String` 和順序的物件 `int32` 。</span><span class="sxs-lookup"><span data-stu-id="759e6-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="759e6-112">ELEMENT_TYPE_FNPTR：所包含的型別參數數目將會大於函式 `ICorDebugTypeEnum` 接受的引數數目。</span><span class="sxs-lookup"><span data-stu-id="759e6-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="759e6-113">包含在中的第一個型別參數是函式 `ICorDebugTypeEnum` 的傳回型別，而後續的型別參數則是函數的參數。</span><span class="sxs-lookup"><span data-stu-id="759e6-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="759e6-114">ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR：將會傳回一個類型參數。</span><span class="sxs-lookup"><span data-stu-id="759e6-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="759e6-115">例如，如果類型是陣列類型（例如 `int32[]` ）， `EnumerateTypeParameters` 則會傳回， `ICorDebugTypeEnum` 其中包含代表的物件 `int32` 。</span><span class="sxs-lookup"><span data-stu-id="759e6-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="759e6-116">需求</span><span class="sxs-lookup"><span data-stu-id="759e6-116">Requirements</span></span>  

 <span data-ttu-id="759e6-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="759e6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="759e6-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="759e6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="759e6-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="759e6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="759e6-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="759e6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
