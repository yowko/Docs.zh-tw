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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b002aaad65fd5f2a1207700c8de2ca8dd60eec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421875"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="d6c40-102">ICorDebugType::EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="d6c40-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="d6c40-103">取得包含 ICorDebugTypeEnum 介面指標<xref:System.Type>此 ICorDebugType 所參考類別的參數。</span><span class="sxs-lookup"><span data-stu-id="d6c40-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c40-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6c40-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6c40-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6c40-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="d6c40-106">[out]位址指標`ICorDebugTypeEnum`包含類型的參數。</span><span class="sxs-lookup"><span data-stu-id="d6c40-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c40-107">備註</span><span class="sxs-lookup"><span data-stu-id="d6c40-107">Remarks</span></span>  
 <span data-ttu-id="d6c40-108">您可以使用`EnumerateTypeParameters`如果 CorElementType 值傳回[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS、 ELEMENT_TYPE_VALUETYPE、 ELEMENT_TYPE_ARRAY、 ELEMENT_TYPE_SZARRAY、 ELEMENT_TYPE_BYREF、 ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_FNPTR。</span><span class="sxs-lookup"><span data-stu-id="d6c40-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="d6c40-109">參數數目和它們的順序取決於類型：</span><span class="sxs-lookup"><span data-stu-id="d6c40-109">The number of parameters and their order depends on the type:</span></span>  
  
-   <span data-ttu-id="d6c40-110">ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE： 中所包含的型別參數數目`ICorDebugTypeEnum`，此方法傳回時，將取決於對應的類別的型式型別參數數目。</span><span class="sxs-lookup"><span data-stu-id="d6c40-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="d6c40-111">例如，如果類型是`class Dict<String,int32>`，然後`EnumerateTypeParameters`會傳回`ICorDebugTypeEnum`，其中包含代表物件`String`和`int32`序列中。</span><span class="sxs-lookup"><span data-stu-id="d6c40-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
-   <span data-ttu-id="d6c40-112">ELEMENT_TYPE_FNPTR: 中所包含的類型參數的數目`ICorDebugTypeEnum`將會大於函式接受引數數目。</span><span class="sxs-lookup"><span data-stu-id="d6c40-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="d6c40-113">中所包含的第一個型別參數`ICorDebugTypeEnum`函數的傳回型別，而後續的型別參數是函式的參數。</span><span class="sxs-lookup"><span data-stu-id="d6c40-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
-   <span data-ttu-id="d6c40-114">ELEMENT_TYPE_ARRAY、 ELEMENT_TYPE_SZARRAY、 ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR： 將會傳回一個型別參數。</span><span class="sxs-lookup"><span data-stu-id="d6c40-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="d6c40-115">例如，如果類型是陣列類型，例如`int32[]`，`EnumerateTypeParameters`會傳回`ICorDebugTypeEnum`，其中包含物件，代表`int32`。</span><span class="sxs-lookup"><span data-stu-id="d6c40-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c40-116">需求</span><span class="sxs-lookup"><span data-stu-id="d6c40-116">Requirements</span></span>  
 <span data-ttu-id="d6c40-117">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c40-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c40-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6c40-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6c40-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6c40-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6c40-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c40-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
