---
title: Get 函式（非受控 API 參考）
description: Get 函式會抓取指定的屬性值。
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17304dc8330e4f8571f25b8544f1049dff229f2b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798588"
---
# <a name="get-function"></a><span data-ttu-id="720fa-103">Get 函式</span><span class="sxs-lookup"><span data-stu-id="720fa-103">Get function</span></span>

<span data-ttu-id="720fa-104">抓取指定的屬性值（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="720fa-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="720fa-105">語法</span><span class="sxs-lookup"><span data-stu-id="720fa-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a><span data-ttu-id="720fa-106">參數</span><span class="sxs-lookup"><span data-stu-id="720fa-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="720fa-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="720fa-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="720fa-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="720fa-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="720fa-109">在屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="720fa-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="720fa-110">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="720fa-110">[in] Reserved.</span></span> <span data-ttu-id="720fa-111">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="720fa-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="720fa-112">脫銷如果函數傳回成功，則包含`wszName`屬性的值。</span><span class="sxs-lookup"><span data-stu-id="720fa-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="720fa-113">已針對限定詞指派正確的類型和值給引數。`pval`</span><span class="sxs-lookup"><span data-stu-id="720fa-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="720fa-114">脫銷如果函式傳回成功，則包含表示屬性類型的[CIM 類型常數](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration)。</span><span class="sxs-lookup"><span data-stu-id="720fa-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="720fa-115">其值也可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="720fa-115">Its value can also be `null`.</span></span> 

`plFlavor`\
<span data-ttu-id="720fa-116">脫銷如果函式傳回成功，會接收屬性來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="720fa-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="720fa-117">其值可以是`null`，或是*WbemCli*標頭檔中所定義的下列其中一個 WBEM_FLAVOR_TYPE 常數：</span><span class="sxs-lookup"><span data-stu-id="720fa-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="720fa-118">常數</span><span class="sxs-lookup"><span data-stu-id="720fa-118">Constant</span></span>  |<span data-ttu-id="720fa-119">值</span><span class="sxs-lookup"><span data-stu-id="720fa-119">Value</span></span>  |<span data-ttu-id="720fa-120">說明</span><span class="sxs-lookup"><span data-stu-id="720fa-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="720fa-121">0x40</span><span class="sxs-lookup"><span data-stu-id="720fa-121">0x40</span></span> | <span data-ttu-id="720fa-122">屬性是標準的系統屬性。</span><span class="sxs-lookup"><span data-stu-id="720fa-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="720fa-123">0x20</span><span class="sxs-lookup"><span data-stu-id="720fa-123">0x20</span></span> | <span data-ttu-id="720fa-124">若為類別：屬性繼承自父類別。</span><span class="sxs-lookup"><span data-stu-id="720fa-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="720fa-125">針對實例：繼承自父類別的屬性尚未由實例修改。</span><span class="sxs-lookup"><span data-stu-id="720fa-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="720fa-126">0</span><span class="sxs-lookup"><span data-stu-id="720fa-126">0</span></span> | <span data-ttu-id="720fa-127">若為類別：屬性屬於衍生類別。</span><span class="sxs-lookup"><span data-stu-id="720fa-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="720fa-128">針對實例：屬性會由實例修改;也就是，已提供值，或已新增或修改限定詞。</span><span class="sxs-lookup"><span data-stu-id="720fa-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="720fa-129">傳回值</span><span class="sxs-lookup"><span data-stu-id="720fa-129">Return value</span></span>

<span data-ttu-id="720fa-130">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="720fa-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="720fa-131">常數</span><span class="sxs-lookup"><span data-stu-id="720fa-131">Constant</span></span>  |<span data-ttu-id="720fa-132">值</span><span class="sxs-lookup"><span data-stu-id="720fa-132">Value</span></span>  |<span data-ttu-id="720fa-133">描述</span><span class="sxs-lookup"><span data-stu-id="720fa-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="720fa-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="720fa-134">0x80041001</span></span> | <span data-ttu-id="720fa-135">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="720fa-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="720fa-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="720fa-136">0x80041008</span></span> | <span data-ttu-id="720fa-137">一或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="720fa-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="720fa-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="720fa-138">0x80041002</span></span> | <span data-ttu-id="720fa-139">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="720fa-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="720fa-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="720fa-140">0x80041006</span></span> | <span data-ttu-id="720fa-141">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="720fa-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="720fa-142">0</span><span class="sxs-lookup"><span data-stu-id="720fa-142">0</span></span> | <span data-ttu-id="720fa-143">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="720fa-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="720fa-144">備註</span><span class="sxs-lookup"><span data-stu-id="720fa-144">Remarks</span></span>

<span data-ttu-id="720fa-145">此函式會包裝對[IWbemClassObject：： Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="720fa-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="720fa-146">`Get`函數也可以傳回系統屬性。</span><span class="sxs-lookup"><span data-stu-id="720fa-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="720fa-147">已針對限定詞和 COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函數指派正確的類型和值給引數`pVal`</span><span class="sxs-lookup"><span data-stu-id="720fa-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="720fa-148">需求</span><span class="sxs-lookup"><span data-stu-id="720fa-148">Requirements</span></span>

 <span data-ttu-id="720fa-149">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="720fa-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="720fa-150">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="720fa-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="720fa-151">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="720fa-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="720fa-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="720fa-152">See also</span></span>

- [<span data-ttu-id="720fa-153">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="720fa-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
