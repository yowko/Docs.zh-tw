---
title: Get 函式 （Unmanaged API 參考）
description: Get 函式，擷取指定的屬性值。
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
ms.openlocfilehash: 2f837a526879f80177bc9979e1d7671edfcd8d4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460144"
---
# <a name="get-function"></a><span data-ttu-id="43e34-103">Get 函式</span><span class="sxs-lookup"><span data-stu-id="43e34-103">Get function</span></span>
<span data-ttu-id="43e34-104">如果存在的話，擷取指定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="43e34-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="43e34-105">語法</span><span class="sxs-lookup"><span data-stu-id="43e34-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="43e34-106">參數</span><span class="sxs-lookup"><span data-stu-id="43e34-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="43e34-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="43e34-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="43e34-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="43e34-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="43e34-109">[in]屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="43e34-109">[in] The name of the property.</span></span>

<span data-ttu-id="43e34-110">`lFlags` [in]保留。</span><span class="sxs-lookup"><span data-stu-id="43e34-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="43e34-111">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="43e34-111">This parameter must be 0.</span></span>

<span data-ttu-id="43e34-112">`pVal` [out]如果此函數會傳回成功，則包含值的`wszName`屬性。</span><span class="sxs-lookup"><span data-stu-id="43e34-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="43e34-113">`pval`引數指派正確的型別和辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="43e34-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="43e34-114">`pvtType` [out]如果此函數會傳回成功，就會包含[CIM 類型常數](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx)，指出此屬性型別。</span><span class="sxs-lookup"><span data-stu-id="43e34-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) that indicates the property type.</span></span> <span data-ttu-id="43e34-115">其值也可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="43e34-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="43e34-116">`plFlavor` [out]如果此函數會傳回成功，接收有關的資訊來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="43e34-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="43e34-117">其值可以是`null`，或其中一個定義中的下列 WBEM_FLAVOR_TYPE 常數*WbemCli.h*標頭檔：</span><span class="sxs-lookup"><span data-stu-id="43e34-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="43e34-118">常數</span><span class="sxs-lookup"><span data-stu-id="43e34-118">Constant</span></span>  |<span data-ttu-id="43e34-119">值</span><span class="sxs-lookup"><span data-stu-id="43e34-119">Value</span></span>  |<span data-ttu-id="43e34-120">描述</span><span class="sxs-lookup"><span data-stu-id="43e34-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="43e34-121">0x40</span><span class="sxs-lookup"><span data-stu-id="43e34-121">0x40</span></span> | <span data-ttu-id="43e34-122">屬性是標準的系統屬性。</span><span class="sxs-lookup"><span data-stu-id="43e34-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="43e34-123">0x20</span><span class="sxs-lookup"><span data-stu-id="43e34-123">0x20</span></span> | <span data-ttu-id="43e34-124">類別： 屬性繼承自父類別。</span><span class="sxs-lookup"><span data-stu-id="43e34-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="43e34-125">執行個體： 屬性繼承自父類別，而尚未修改的執行個體。</span><span class="sxs-lookup"><span data-stu-id="43e34-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="43e34-126">0</span><span class="sxs-lookup"><span data-stu-id="43e34-126">0</span></span> | <span data-ttu-id="43e34-127">類別： 屬性屬於衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="43e34-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="43e34-128">執行個體： 執行個體; 所修改的屬性也就是所提供的值，或辨識符號的加入或修改。</span><span class="sxs-lookup"><span data-stu-id="43e34-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="43e34-129">傳回值</span><span class="sxs-lookup"><span data-stu-id="43e34-129">Return value</span></span>

<span data-ttu-id="43e34-130">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="43e34-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="43e34-131">常數</span><span class="sxs-lookup"><span data-stu-id="43e34-131">Constant</span></span>  |<span data-ttu-id="43e34-132">值</span><span class="sxs-lookup"><span data-stu-id="43e34-132">Value</span></span>  |<span data-ttu-id="43e34-133">描述</span><span class="sxs-lookup"><span data-stu-id="43e34-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="43e34-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="43e34-134">0x80041001</span></span> | <span data-ttu-id="43e34-135">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="43e34-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="43e34-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="43e34-136">0x80041008</span></span> | <span data-ttu-id="43e34-137">一或多個參數都不是有效的。</span><span class="sxs-lookup"><span data-stu-id="43e34-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="43e34-138">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="43e34-138">0x80041002</span></span> | <span data-ttu-id="43e34-139">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="43e34-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="43e34-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="43e34-140">0x80041006</span></span> | <span data-ttu-id="43e34-141">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="43e34-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="43e34-142">0</span><span class="sxs-lookup"><span data-stu-id="43e34-142">0</span></span> | <span data-ttu-id="43e34-143">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="43e34-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="43e34-144">備註</span><span class="sxs-lookup"><span data-stu-id="43e34-144">Remarks</span></span>

<span data-ttu-id="43e34-145">此函式會包裝呼叫[IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="43e34-145">This function wraps a call to the [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="43e34-146">`Get`函式也可以傳回系統屬性。</span><span class="sxs-lookup"><span data-stu-id="43e34-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="43e34-147">`pVal`引數指派正確的型別和值限定詞和 COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx)函式</span><span class="sxs-lookup"><span data-stu-id="43e34-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) function</span></span>

## <a name="requirements"></a><span data-ttu-id="43e34-148">需求</span><span class="sxs-lookup"><span data-stu-id="43e34-148">Requirements</span></span>  
 <span data-ttu-id="43e34-149">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43e34-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43e34-150">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="43e34-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="43e34-151">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="43e34-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e34-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43e34-152">See also</span></span>  
[<span data-ttu-id="43e34-153">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="43e34-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
