---
title: ICorDebugEval::CreateValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c16f6d1334888fc389a7c39cf0a3865afca2085
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471040"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="4725d-102">ICorDebugEval::CreateValue 方法</span><span class="sxs-lookup"><span data-stu-id="4725d-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="4725d-103">建立具有的值指定的類型，初始值為零或 null。</span><span class="sxs-lookup"><span data-stu-id="4725d-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="4725d-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="4725d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="4725d-105">使用[ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="4725d-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4725d-106">語法</span><span class="sxs-lookup"><span data-stu-id="4725d-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4725d-107">參數</span><span class="sxs-lookup"><span data-stu-id="4725d-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="4725d-108">[in]值為[CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列舉，指定值的類型。</span><span class="sxs-lookup"><span data-stu-id="4725d-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="4725d-109">[in]指標[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)物件，如果類型不是基本型別指定值的類別。</span><span class="sxs-lookup"><span data-stu-id="4725d-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4725d-110">[out]表示值的"ICorDebugValue 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="4725d-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4725d-111">備註</span><span class="sxs-lookup"><span data-stu-id="4725d-111">Remarks</span></span>  
 <span data-ttu-id="4725d-112">`CreateValue` 建立`ICorDebugValue`用途使用函式評估中的指定型別的物件。</span><span class="sxs-lookup"><span data-stu-id="4725d-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="4725d-113">此值物件可用來做為參數傳遞使用者常數。</span><span class="sxs-lookup"><span data-stu-id="4725d-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="4725d-114">如果值的型別是基本型別，其初始值為零，則為 null。</span><span class="sxs-lookup"><span data-stu-id="4725d-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="4725d-115">使用[icordebuggenericvalue:: Setvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)設定基本類型的值。</span><span class="sxs-lookup"><span data-stu-id="4725d-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="4725d-116">如果值`elementType`是 ELEMENT_TYPE_CLASS，取得"ICorDebugReferenceValue 」 (傳入`ppValue`) 代表 null 物件參考。</span><span class="sxs-lookup"><span data-stu-id="4725d-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="4725d-117">您可以使用這個物件將 null 傳遞至函式評估的物件參考參數。</span><span class="sxs-lookup"><span data-stu-id="4725d-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="4725d-118">您不能設定`ICorDebugValue`到任何項目，它一定會保持為 null。</span><span class="sxs-lookup"><span data-stu-id="4725d-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4725d-119">需求</span><span class="sxs-lookup"><span data-stu-id="4725d-119">Requirements</span></span>  
 <span data-ttu-id="4725d-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4725d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4725d-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4725d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4725d-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4725d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4725d-123">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="4725d-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4725d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4725d-124">See also</span></span>

- [<span data-ttu-id="4725d-125">CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="4725d-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="4725d-126">ICorDebugEval 介面</span><span class="sxs-lookup"><span data-stu-id="4725d-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
