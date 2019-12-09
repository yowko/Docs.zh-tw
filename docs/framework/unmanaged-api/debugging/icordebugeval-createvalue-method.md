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
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085141"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="18624-102">ICorDebugEval::CreateValue 方法</span><span class="sxs-lookup"><span data-stu-id="18624-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="18624-103">建立指定類型的值，其初始值為零或 null。</span><span class="sxs-lookup"><span data-stu-id="18624-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="18624-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="18624-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="18624-105">請改用[ICorDebugEval2：： CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="18624-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18624-106">語法</span><span class="sxs-lookup"><span data-stu-id="18624-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18624-107">參數</span><span class="sxs-lookup"><span data-stu-id="18624-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="18624-108">在[CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列舉的值，指定值的類型。</span><span class="sxs-lookup"><span data-stu-id="18624-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="18624-109">在如果類型不是基本型別，則為指定值之類別的[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)物件指標。</span><span class="sxs-lookup"><span data-stu-id="18624-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="18624-110">脫銷表示值之 "ICorDebugValue" 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="18624-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18624-111">備註</span><span class="sxs-lookup"><span data-stu-id="18624-111">Remarks</span></span>  
 <span data-ttu-id="18624-112">`CreateValue` 會建立給定類型的 `ICorDebugValue` 物件，以在函數評估中使用它的唯一目的。</span><span class="sxs-lookup"><span data-stu-id="18624-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="18624-113">這個值物件可以用來傳遞使用者常數做為參數。</span><span class="sxs-lookup"><span data-stu-id="18624-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="18624-114">如果值的類型是基本類型，其初始值為零或 null。</span><span class="sxs-lookup"><span data-stu-id="18624-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="18624-115">請使用[ICorDebugGenericValue：： SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)來設定基本類型的值。</span><span class="sxs-lookup"><span data-stu-id="18624-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="18624-116">如果 `elementType` 的值為 ELEMENT_TYPE_CLASS，您會取得代表 null 物件參考的 "ICorDebugReferenceValue" （在 `ppValue`中傳回）。</span><span class="sxs-lookup"><span data-stu-id="18624-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="18624-117">您可以使用這個物件，將 null 傳遞給具有物件參考參數的函式評估。</span><span class="sxs-lookup"><span data-stu-id="18624-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="18624-118">您不能將 `ICorDebugValue` 設定為任何專案;它一律會保持為 null。</span><span class="sxs-lookup"><span data-stu-id="18624-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18624-119">需求</span><span class="sxs-lookup"><span data-stu-id="18624-119">Requirements</span></span>  
 <span data-ttu-id="18624-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18624-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18624-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18624-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18624-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18624-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18624-123">**.NET Framework 版本：** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="18624-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18624-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="18624-124">See also</span></span>

- [<span data-ttu-id="18624-125">CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="18624-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="18624-126">ICorDebugEval 介面</span><span class="sxs-lookup"><span data-stu-id="18624-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
