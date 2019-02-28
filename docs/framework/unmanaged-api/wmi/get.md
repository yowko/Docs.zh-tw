---
title: Get 函式 （Unmanaged API 參考）
description: Get 函式會擷取指定之的屬性的值。
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
ms.openlocfilehash: e996a299de7b365a1513d5b1fb7ca0e758f6005b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966056"
---
# <a name="get-function"></a><span data-ttu-id="e26d5-103">Get 函式</span><span class="sxs-lookup"><span data-stu-id="e26d5-103">Get function</span></span>
<span data-ttu-id="e26d5-104">若有的話，則擷取指定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="e26d5-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e26d5-105">語法</span><span class="sxs-lookup"><span data-stu-id="e26d5-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="e26d5-106">參數</span><span class="sxs-lookup"><span data-stu-id="e26d5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e26d5-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="e26d5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e26d5-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="e26d5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="e26d5-109">[in]屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e26d5-109">[in] The name of the property.</span></span>

<span data-ttu-id="e26d5-110">`lFlags` [in]保留。</span><span class="sxs-lookup"><span data-stu-id="e26d5-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="e26d5-111">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="e26d5-111">This parameter must be 0.</span></span>

<span data-ttu-id="e26d5-112">`pVal` [out]如果函式會傳回成功，則包含值的`wszName`屬性。</span><span class="sxs-lookup"><span data-stu-id="e26d5-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="e26d5-113">`pval`引數指派正確的型別和辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="e26d5-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="e26d5-114">`pvtType` [out]如果函式會傳回成功，就會包含[CIM 類型常數](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration)表示的屬性型別。</span><span class="sxs-lookup"><span data-stu-id="e26d5-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="e26d5-115">其值也可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="e26d5-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="e26d5-116">`plFlavor` [out]如果函式會傳回成功，會收到之屬性的原點資訊。</span><span class="sxs-lookup"><span data-stu-id="e26d5-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="e26d5-117">其值可以是`null`，或其中一個定義中的下列 WBEM_FLAVOR_TYPE 常數*WbemCli.h*標頭檔：</span><span class="sxs-lookup"><span data-stu-id="e26d5-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="e26d5-118">常數</span><span class="sxs-lookup"><span data-stu-id="e26d5-118">Constant</span></span>  |<span data-ttu-id="e26d5-119">值</span><span class="sxs-lookup"><span data-stu-id="e26d5-119">Value</span></span>  |<span data-ttu-id="e26d5-120">描述</span><span class="sxs-lookup"><span data-stu-id="e26d5-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="e26d5-121">0x40</span><span class="sxs-lookup"><span data-stu-id="e26d5-121">0x40</span></span> | <span data-ttu-id="e26d5-122">屬性是標準的系統屬性。</span><span class="sxs-lookup"><span data-stu-id="e26d5-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="e26d5-123">0x20</span><span class="sxs-lookup"><span data-stu-id="e26d5-123">0x20</span></span> | <span data-ttu-id="e26d5-124">類別：屬性被繼承自父類別。</span><span class="sxs-lookup"><span data-stu-id="e26d5-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="e26d5-125">執行個體：屬性，而繼承自父類別中，有尚未修改的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e26d5-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="e26d5-126">0</span><span class="sxs-lookup"><span data-stu-id="e26d5-126">0</span></span> | <span data-ttu-id="e26d5-127">類別：屬性屬於衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="e26d5-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="e26d5-128">執行個體：執行個體; 所修改的屬性也就是所提供的值，或加入或修改限定詞。</span><span class="sxs-lookup"><span data-stu-id="e26d5-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e26d5-129">傳回值</span><span class="sxs-lookup"><span data-stu-id="e26d5-129">Return value</span></span>

<span data-ttu-id="e26d5-130">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="e26d5-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e26d5-131">常數</span><span class="sxs-lookup"><span data-stu-id="e26d5-131">Constant</span></span>  |<span data-ttu-id="e26d5-132">值</span><span class="sxs-lookup"><span data-stu-id="e26d5-132">Value</span></span>  |<span data-ttu-id="e26d5-133">描述</span><span class="sxs-lookup"><span data-stu-id="e26d5-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e26d5-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e26d5-134">0x80041001</span></span> | <span data-ttu-id="e26d5-135">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="e26d5-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e26d5-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e26d5-136">0x80041008</span></span> | <span data-ttu-id="e26d5-137">找不到有效的一或多個參數。</span><span class="sxs-lookup"><span data-stu-id="e26d5-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e26d5-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e26d5-138">0x80041002</span></span> | <span data-ttu-id="e26d5-139">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="e26d5-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e26d5-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e26d5-140">0x80041006</span></span> | <span data-ttu-id="e26d5-141">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="e26d5-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e26d5-142">0</span><span class="sxs-lookup"><span data-stu-id="e26d5-142">0</span></span> | <span data-ttu-id="e26d5-143">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e26d5-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e26d5-144">備註</span><span class="sxs-lookup"><span data-stu-id="e26d5-144">Remarks</span></span>

<span data-ttu-id="e26d5-145">此函式會包裝在呼叫[IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)方法。</span><span class="sxs-lookup"><span data-stu-id="e26d5-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="e26d5-146">`Get`函式也可以傳回系統屬性。</span><span class="sxs-lookup"><span data-stu-id="e26d5-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="e26d5-147">`pVal`引數指派正確的型別和值限定詞和 COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函式</span><span class="sxs-lookup"><span data-stu-id="e26d5-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="e26d5-148">需求</span><span class="sxs-lookup"><span data-stu-id="e26d5-148">Requirements</span></span>  
 <span data-ttu-id="e26d5-149">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e26d5-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e26d5-150">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e26d5-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e26d5-151">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e26d5-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e26d5-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e26d5-152">See also</span></span>
- [<span data-ttu-id="e26d5-153">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="e26d5-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
