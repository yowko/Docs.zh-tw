---
title: Put 函數（非受控 API 參考）
description: Put 函式會將新值指派給已命名的屬性。
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
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798393"
---
# <a name="put-function"></a><span data-ttu-id="107da-103">Put 函式</span><span class="sxs-lookup"><span data-stu-id="107da-103">Put function</span></span>

<span data-ttu-id="107da-104">將具名屬性設定為新值。</span><span class="sxs-lookup"><span data-stu-id="107da-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="107da-105">語法</span><span class="sxs-lookup"><span data-stu-id="107da-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="107da-106">參數</span><span class="sxs-lookup"><span data-stu-id="107da-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="107da-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="107da-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="107da-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="107da-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="107da-109">在屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="107da-109">[in] The name of the property.</span></span> <span data-ttu-id="107da-110">這個參數不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="107da-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="107da-111">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="107da-111">[in] Reserved.</span></span> <span data-ttu-id="107da-112">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="107da-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="107da-113">在有效`VARIANT`的指標，它會成為新的屬性值。</span><span class="sxs-lookup"><span data-stu-id="107da-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="107da-114">如果`pVal` `VARIANT`為`null` ，或指向`null`類型`VT_NULL`的，則屬性會設定為。</span><span class="sxs-lookup"><span data-stu-id="107da-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="107da-115">在所`VARIANT` 指向`pVal`的類型。</span><span class="sxs-lookup"><span data-stu-id="107da-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="107da-116">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="107da-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="107da-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="107da-117">Return value</span></span>

<span data-ttu-id="107da-118">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="107da-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="107da-119">常數</span><span class="sxs-lookup"><span data-stu-id="107da-119">Constant</span></span>  |<span data-ttu-id="107da-120">值</span><span class="sxs-lookup"><span data-stu-id="107da-120">Value</span></span>  |<span data-ttu-id="107da-121">描述</span><span class="sxs-lookup"><span data-stu-id="107da-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="107da-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="107da-122">0x80041001</span></span> | <span data-ttu-id="107da-123">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="107da-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="107da-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="107da-124">0x80041008</span></span> | <span data-ttu-id="107da-125">一或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="107da-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="107da-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="107da-126">0x8004102a</span></span> | <span data-ttu-id="107da-127">無法辨識屬性類型。</span><span class="sxs-lookup"><span data-stu-id="107da-127">The property type is not recognized.</span></span> <span data-ttu-id="107da-128">建立類別實例時，如果類別已經存在，就會傳回這個值。</span><span class="sxs-lookup"><span data-stu-id="107da-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="107da-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="107da-129">0x80041006</span></span> | <span data-ttu-id="107da-130">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="107da-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="107da-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="107da-131">0x80041005</span></span> | <span data-ttu-id="107da-132">針對實例：`pVal`表示指向`VARIANT`屬性的不正確類型的。</span><span class="sxs-lookup"><span data-stu-id="107da-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="107da-133">針對類別定義：屬性已經存在於父類別中，而新的 COM 類型與舊的 COM 類型不同。</span><span class="sxs-lookup"><span data-stu-id="107da-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="107da-134">0</span><span class="sxs-lookup"><span data-stu-id="107da-134">0</span></span> | <span data-ttu-id="107da-135">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="107da-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="107da-136">備註</span><span class="sxs-lookup"><span data-stu-id="107da-136">Remarks</span></span>

<span data-ttu-id="107da-137">此函式會包裝對[IWbemClassObject：:P](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)的工作方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="107da-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="107da-138">此函式一律會以新的屬性值覆寫。</span><span class="sxs-lookup"><span data-stu-id="107da-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="107da-139">如果[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向類別定義， `Put`則會建立或更新屬性值。</span><span class="sxs-lookup"><span data-stu-id="107da-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="107da-140">當[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向 CIM 實例時， `Put`只會更新屬性值。`Put`無法建立屬性值。</span><span class="sxs-lookup"><span data-stu-id="107da-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="107da-141">只有在類別建立期間，系統屬性可能不會保留空白時，才可寫入。`__CLASS`</span><span class="sxs-lookup"><span data-stu-id="107da-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="107da-142">所有其他的系統屬性都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="107da-142">All other system properties are read-only.</span></span>

<span data-ttu-id="107da-143">使用者無法以底線（"_"）來建立名稱開頭或結尾的屬性。</span><span class="sxs-lookup"><span data-stu-id="107da-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="107da-144">這會保留給系統類別和屬性。</span><span class="sxs-lookup"><span data-stu-id="107da-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="107da-145">如果函式所設定`Put`的屬性存在於父類別中，除非屬性類型與父類別類型不相符，否則屬性的預設值會變更。</span><span class="sxs-lookup"><span data-stu-id="107da-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="107da-146">如果屬性不存在，而且不是類型不符，則會建立屬性。</span><span class="sxs-lookup"><span data-stu-id="107da-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="107da-147">`VARIANT` `pVal` `null`只有在 CIM 類別定義中建立新屬性，且為或指向類型`VT_NULL`的時，才使用參數。`vtType`</span><span class="sxs-lookup"><span data-stu-id="107da-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="107da-148">在此情況下， `vType`參數會指定屬性的 CIM 類型。</span><span class="sxs-lookup"><span data-stu-id="107da-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="107da-149">在其他所有情況下`vtType` ，必須是0。</span><span class="sxs-lookup"><span data-stu-id="107da-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="107da-150">`vtType`如果基礎物件是實例（即使`Val`是`null`），則也必須是0，因為屬性的類型是固定的，而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="107da-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="107da-151">範例</span><span class="sxs-lookup"><span data-stu-id="107da-151">Example</span></span>

<span data-ttu-id="107da-152">如需範例，請參閱[IWbemClassObject：:P](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)的工作方法。</span><span class="sxs-lookup"><span data-stu-id="107da-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="107da-153">需求</span><span class="sxs-lookup"><span data-stu-id="107da-153">Requirements</span></span>

<span data-ttu-id="107da-154">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="107da-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="107da-155">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="107da-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="107da-156">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="107da-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="107da-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="107da-157">See also</span></span>

- [<span data-ttu-id="107da-158">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="107da-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
