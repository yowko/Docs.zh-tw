---
title: Put 函式 （Unmanaged API 參考）
description: Put 函式會將新的值指派給具名屬性。
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02c8ab3aa7fcc603b76fb4b1d09e7e73d04494be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749016"
---
# <a name="put-function"></a><span data-ttu-id="8e973-103">Put 函式</span><span class="sxs-lookup"><span data-stu-id="8e973-103">Put function</span></span>

<span data-ttu-id="8e973-104">將具名屬性設定為新值。</span><span class="sxs-lookup"><span data-stu-id="8e973-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8e973-105">語法</span><span class="sxs-lookup"><span data-stu-id="8e973-105">Syntax</span></span>

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a><span data-ttu-id="8e973-106">參數</span><span class="sxs-lookup"><span data-stu-id="8e973-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="8e973-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="8e973-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="8e973-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e973-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="8e973-109">[in]屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e973-109">[in] The name of the property.</span></span> <span data-ttu-id="8e973-110">這個參數不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="8e973-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="8e973-111">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="8e973-111">[in] Reserved.</span></span> <span data-ttu-id="8e973-112">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="8e973-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="8e973-113">[in]有效的指標`VARIANT`會變成新的屬性值。</span><span class="sxs-lookup"><span data-stu-id="8e973-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="8e973-114">如果`pVal`是`null`或指向`VARIANT`型別的`VT_NULL`，屬性設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="8e973-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="8e973-115">[in]型別`VARIANT`所指向`pVal`。</span><span class="sxs-lookup"><span data-stu-id="8e973-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="8e973-116">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8e973-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="8e973-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e973-117">Return value</span></span>

<span data-ttu-id="8e973-118">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="8e973-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8e973-119">常數</span><span class="sxs-lookup"><span data-stu-id="8e973-119">Constant</span></span>  |<span data-ttu-id="8e973-120">值</span><span class="sxs-lookup"><span data-stu-id="8e973-120">Value</span></span>  |<span data-ttu-id="8e973-121">描述</span><span class="sxs-lookup"><span data-stu-id="8e973-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8e973-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8e973-122">0x80041001</span></span> | <span data-ttu-id="8e973-123">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="8e973-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8e973-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8e973-124">0x80041008</span></span> | <span data-ttu-id="8e973-125">找不到有效的一或多個參數。</span><span class="sxs-lookup"><span data-stu-id="8e973-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="8e973-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="8e973-126">0x8004102a</span></span> | <span data-ttu-id="8e973-127">無法辨識的屬性型別。</span><span class="sxs-lookup"><span data-stu-id="8e973-127">The property type is not recognized.</span></span> <span data-ttu-id="8e973-128">建立類別執行個體，如果類別已存在時，會傳回此值。</span><span class="sxs-lookup"><span data-stu-id="8e973-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8e973-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8e973-129">0x80041006</span></span> | <span data-ttu-id="8e973-130">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="8e973-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="8e973-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="8e973-131">0x80041005</span></span> | <span data-ttu-id="8e973-132">執行個體：指出`pVal`指向`VARIANT`屬性的型別不正確。</span><span class="sxs-lookup"><span data-stu-id="8e973-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="8e973-133">如需類別定義：屬性中已存在的父類別，新的 COM 型別是從舊的 COM 型別不同。</span><span class="sxs-lookup"><span data-stu-id="8e973-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8e973-134">0</span><span class="sxs-lookup"><span data-stu-id="8e973-134">0</span></span> | <span data-ttu-id="8e973-135">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="8e973-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8e973-136">備註</span><span class="sxs-lookup"><span data-stu-id="8e973-136">Remarks</span></span>

<span data-ttu-id="8e973-137">此函式會包裝在呼叫[IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)方法。</span><span class="sxs-lookup"><span data-stu-id="8e973-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="8e973-138">此函式一律覆寫一個新的目前屬性值。</span><span class="sxs-lookup"><span data-stu-id="8e973-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="8e973-139">如果[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向類別定義，`Put`建立或更新的屬性值。</span><span class="sxs-lookup"><span data-stu-id="8e973-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="8e973-140">當[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向 CIM 的執行個體，`Put`更新屬性值;`Put`無法建立屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8e973-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="8e973-141">`__CLASS`系統屬性時，只可寫入類別在建立期間，它可能不能空白。</span><span class="sxs-lookup"><span data-stu-id="8e973-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="8e973-142">所有其他的系統屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="8e973-142">All other system properties are read-only.</span></span>

<span data-ttu-id="8e973-143">使用者無法建立屬性，其開頭或結尾底線 ("_") 的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e973-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="8e973-144">這被保留給系統的類別和屬性。</span><span class="sxs-lookup"><span data-stu-id="8e973-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="8e973-145">如果設定的屬性`Put`函式父類別中，屬性的預設值已變更，除非屬性型別不符的父類別型別。</span><span class="sxs-lookup"><span data-stu-id="8e973-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="8e973-146">如果屬性不存在，而且它不是類型不符，則會建立屬性。</span><span class="sxs-lookup"><span data-stu-id="8e973-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="8e973-147">使用`vtType`只有在 CIM 類別定義中建立新的屬性時的參數和`pVal`是`null`或指向`VARIANT`型別的`VT_NULL`。</span><span class="sxs-lookup"><span data-stu-id="8e973-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="8e973-148">在此情況下，`vType`參數指定之屬性的 CIM 型別。</span><span class="sxs-lookup"><span data-stu-id="8e973-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="8e973-149">在每個其他情況下，`vtType`必須是 0。</span><span class="sxs-lookup"><span data-stu-id="8e973-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="8e973-150">`vtType` 如果基礎的物件執行個體，則也必須是 0 (即使`Val`是`null`) 因為屬性的型別固定的無法變更。</span><span class="sxs-lookup"><span data-stu-id="8e973-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="8e973-151">範例</span><span class="sxs-lookup"><span data-stu-id="8e973-151">Example</span></span>

<span data-ttu-id="8e973-152">如需範例，請參閱[IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)方法。</span><span class="sxs-lookup"><span data-stu-id="8e973-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8e973-153">需求</span><span class="sxs-lookup"><span data-stu-id="8e973-153">Requirements</span></span>

<span data-ttu-id="8e973-154">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e973-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="8e973-155">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8e973-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="8e973-156">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8e973-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8e973-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e973-157">See also</span></span>

- [<span data-ttu-id="8e973-158">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="8e973-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)