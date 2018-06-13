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
ms.openlocfilehash: 6d67784daee055106f104d74d098b9926c6de2ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417108"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="11130-102">ICorDebugEval::CreateValue 方法</span><span class="sxs-lookup"><span data-stu-id="11130-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="11130-103">建立指定類型的值，其初始值為零或 null。</span><span class="sxs-lookup"><span data-stu-id="11130-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="11130-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="11130-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="11130-105">使用[icordebugeval2:: Createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="11130-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11130-106">語法</span><span class="sxs-lookup"><span data-stu-id="11130-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11130-107">參數</span><span class="sxs-lookup"><span data-stu-id="11130-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="11130-108">[in]值為[CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列舉，指定值的類型。</span><span class="sxs-lookup"><span data-stu-id="11130-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="11130-109">[in]指標[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)物件，指定類別的值，如果型別不是 primitive 類型。</span><span class="sxs-lookup"><span data-stu-id="11130-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="11130-110">[out]表示值的"ICorDebugValue 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="11130-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11130-111">備註</span><span class="sxs-lookup"><span data-stu-id="11130-111">Remarks</span></span>  
 <span data-ttu-id="11130-112">`CreateValue` 建立`ICorDebugValue`只是為了在使用中函式評估的指定型別的物件。</span><span class="sxs-lookup"><span data-stu-id="11130-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="11130-113">此值的物件可以用來做為參數傳遞使用者常數。</span><span class="sxs-lookup"><span data-stu-id="11130-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="11130-114">如果值的型別是基本型別，其初始值為零，則為 null。</span><span class="sxs-lookup"><span data-stu-id="11130-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="11130-115">使用[icordebuggenericvalue:: Setvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)設定基本類型的值。</span><span class="sxs-lookup"><span data-stu-id="11130-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="11130-116">如果值`elementType`是 ELEMENT_TYPE_CLASS，取得"ICorDebugReferenceValue 」 (傳回`ppValue`) 代表 null 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="11130-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="11130-117">您可以使用這個物件將 null 傳遞至具有物件參考參數的函式評估。</span><span class="sxs-lookup"><span data-stu-id="11130-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="11130-118">您不能設定`ICorDebugValue`到任何項目，它一定會保持為 null。</span><span class="sxs-lookup"><span data-stu-id="11130-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11130-119">需求</span><span class="sxs-lookup"><span data-stu-id="11130-119">Requirements</span></span>  
 <span data-ttu-id="11130-120">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11130-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11130-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11130-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11130-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11130-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11130-123">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="11130-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11130-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11130-124">See Also</span></span>  
    
 [<span data-ttu-id="11130-125">CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="11130-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 <span data-ttu-id="11130-126">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="11130-126">ICorDebugValue</span></span>
