---
title: 獲取功能（非託管 API 引用）
description: Get 函數檢索指定的屬性值。
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
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174975"
---
# <a name="get-function"></a><span data-ttu-id="92671-103">Get 函式</span><span class="sxs-lookup"><span data-stu-id="92671-103">Get function</span></span>

<span data-ttu-id="92671-104">如果指定的屬性值存在，則檢索該值。</span><span class="sxs-lookup"><span data-stu-id="92671-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="92671-105">語法</span><span class="sxs-lookup"><span data-stu-id="92671-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="92671-106">參數</span><span class="sxs-lookup"><span data-stu-id="92671-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="92671-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="92671-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="92671-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="92671-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="92671-109">[在]屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="92671-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="92671-110">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="92671-110">[in] Reserved.</span></span> <span data-ttu-id="92671-111">此參數必須為 0。</span><span class="sxs-lookup"><span data-stu-id="92671-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="92671-112">[出]如果函數成功返回，則包含`wszName`屬性的值。</span><span class="sxs-lookup"><span data-stu-id="92671-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="92671-113">為`pval`限定詞分配了正確的類型和值。</span><span class="sxs-lookup"><span data-stu-id="92671-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="92671-114">[出]如果函數成功返回，則包含指示屬性類型的[CIM 類型常量](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration)。</span><span class="sxs-lookup"><span data-stu-id="92671-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="92671-115">其值也可以`null`是 。</span><span class="sxs-lookup"><span data-stu-id="92671-115">Its value can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="92671-116">[出]如果函數成功返回，則接收有關屬性源的資訊。</span><span class="sxs-lookup"><span data-stu-id="92671-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="92671-117">其值可以是`null`，或者*WbemCli.h*標標頭檔中定義的以下WBEM_FLAVOR_TYPE常量之一：</span><span class="sxs-lookup"><span data-stu-id="92671-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span>

|<span data-ttu-id="92671-118">持續性</span><span class="sxs-lookup"><span data-stu-id="92671-118">Constant</span></span>  |<span data-ttu-id="92671-119">值</span><span class="sxs-lookup"><span data-stu-id="92671-119">Value</span></span>  |<span data-ttu-id="92671-120">描述</span><span class="sxs-lookup"><span data-stu-id="92671-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="92671-121">0x40</span><span class="sxs-lookup"><span data-stu-id="92671-121">0x40</span></span> | <span data-ttu-id="92671-122">屬性是標準系統屬性。</span><span class="sxs-lookup"><span data-stu-id="92671-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="92671-123">0x20</span><span class="sxs-lookup"><span data-stu-id="92671-123">0x20</span></span> | <span data-ttu-id="92671-124">對於類：屬性是從父類繼承的。</span><span class="sxs-lookup"><span data-stu-id="92671-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="92671-125">對於實例：屬性雖然從父類繼承，但實例尚未修改。</span><span class="sxs-lookup"><span data-stu-id="92671-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="92671-126">0</span><span class="sxs-lookup"><span data-stu-id="92671-126">0</span></span> | <span data-ttu-id="92671-127">對於類：屬性屬於派生類。</span><span class="sxs-lookup"><span data-stu-id="92671-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="92671-128">對於實例：屬性由實例修改;但是，該屬性由 實例修改。即，提供了值，或者添加或修改了限定詞。</span><span class="sxs-lookup"><span data-stu-id="92671-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="92671-129">傳回值</span><span class="sxs-lookup"><span data-stu-id="92671-129">Return value</span></span>

<span data-ttu-id="92671-130">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="92671-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="92671-131">持續性</span><span class="sxs-lookup"><span data-stu-id="92671-131">Constant</span></span>  |<span data-ttu-id="92671-132">值</span><span class="sxs-lookup"><span data-stu-id="92671-132">Value</span></span>  |<span data-ttu-id="92671-133">描述</span><span class="sxs-lookup"><span data-stu-id="92671-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="92671-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="92671-134">0x80041001</span></span> | <span data-ttu-id="92671-135">出現了一個普遍的失敗。</span><span class="sxs-lookup"><span data-stu-id="92671-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="92671-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="92671-136">0x80041008</span></span> | <span data-ttu-id="92671-137">一個或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="92671-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="92671-138">0 x80041002</span><span class="sxs-lookup"><span data-stu-id="92671-138">0x80041002</span></span> | <span data-ttu-id="92671-139">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="92671-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="92671-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="92671-140">0x80041006</span></span> | <span data-ttu-id="92671-141">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="92671-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="92671-142">0</span><span class="sxs-lookup"><span data-stu-id="92671-142">0</span></span> | <span data-ttu-id="92671-143">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="92671-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="92671-144">備註</span><span class="sxs-lookup"><span data-stu-id="92671-144">Remarks</span></span>

<span data-ttu-id="92671-145">此函數包裝對[IWbem ClassObject 的調用：：get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)方法。</span><span class="sxs-lookup"><span data-stu-id="92671-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="92671-146">該`Get`函數還可以返回系統屬性。</span><span class="sxs-lookup"><span data-stu-id="92671-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="92671-147">為`pVal`限定詞和 COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函數分配了正確的類型和值</span><span class="sxs-lookup"><span data-stu-id="92671-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="92671-148">需求</span><span class="sxs-lookup"><span data-stu-id="92671-148">Requirements</span></span>

 <span data-ttu-id="92671-149">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92671-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="92671-150">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="92671-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="92671-151">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92671-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="92671-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92671-152">See also</span></span>

- [<span data-ttu-id="92671-153">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="92671-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
