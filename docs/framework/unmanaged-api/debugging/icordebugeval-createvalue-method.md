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
ms.openlocfilehash: 41db6ac00d8646651d0e8433d076c37af6020071
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696150"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="63852-102">ICorDebugEval::CreateValue 方法</span><span class="sxs-lookup"><span data-stu-id="63852-102">ICorDebugEval::CreateValue Method</span></span>

<span data-ttu-id="63852-103">建立指定類型的值，其初始值為零或 null。</span><span class="sxs-lookup"><span data-stu-id="63852-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="63852-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="63852-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="63852-105">請改用 [ICorDebugEval2：： CreateValueForType](icordebugeval2-createvaluefortype-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="63852-105">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63852-106">語法</span><span class="sxs-lookup"><span data-stu-id="63852-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63852-107">參數</span><span class="sxs-lookup"><span data-stu-id="63852-107">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="63852-108">在 [CorElementType](../metadata/corelementtype-enumeration.md) 列舉的值，指定值的類型。</span><span class="sxs-lookup"><span data-stu-id="63852-108">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="63852-109">在如果類型不是基本類型，則為指定值之類別的 [ICorDebugClass](icordebugclass-interface.md) 物件指標。</span><span class="sxs-lookup"><span data-stu-id="63852-109">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="63852-110">擴展代表值的 "ICorDebugValue" 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="63852-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63852-111">備註</span><span class="sxs-lookup"><span data-stu-id="63852-111">Remarks</span></span>  

 <span data-ttu-id="63852-112">`CreateValue` 針對在 `ICorDebugValue` 函數評估中使用它的唯一目的，建立指定型別的物件。</span><span class="sxs-lookup"><span data-stu-id="63852-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="63852-113">此值物件可以用來將使用者常數當做參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="63852-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="63852-114">如果值的類型是基本類型，則其初始值為零或 null。</span><span class="sxs-lookup"><span data-stu-id="63852-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="63852-115">使用 [ICorDebugGenericValue：： SetValue](icordebuggenericvalue-setvalue-method.md) 設定基本類型的值。</span><span class="sxs-lookup"><span data-stu-id="63852-115">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="63852-116">如果 ELEMENT_TYPE_CLASS 的值 `elementType` ，您會在) 中取得傳回的 "ICorDebugReferenceValue" (， `ppValue` 表示 null 物件參考。</span><span class="sxs-lookup"><span data-stu-id="63852-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="63852-117">您可以使用此物件，將 null 傳遞給具有物件參考參數的函式評估。</span><span class="sxs-lookup"><span data-stu-id="63852-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="63852-118">您無法將設定為任何值， `ICorDebugValue` 它一律會維持 null。</span><span class="sxs-lookup"><span data-stu-id="63852-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63852-119">需求</span><span class="sxs-lookup"><span data-stu-id="63852-119">Requirements</span></span>  

 <span data-ttu-id="63852-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63852-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63852-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63852-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63852-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63852-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63852-123">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="63852-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63852-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63852-124">See also</span></span>

- [<span data-ttu-id="63852-125">CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="63852-125">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="63852-126">ICorDebugEval 介面</span><span class="sxs-lookup"><span data-stu-id="63852-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
