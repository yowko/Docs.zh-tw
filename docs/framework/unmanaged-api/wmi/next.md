---
title: "下一個函式 （Unmanaged API 參考）"
description: "下一個函式 retireves 列舉中的下一個屬性。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e59ef3f65b75a91708dc65f7d4e3d811dc2d3f9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="next-function"></a><span data-ttu-id="72d91-103">下一個函式</span><span class="sxs-lookup"><span data-stu-id="72d91-103">Next function</span></span>
<span data-ttu-id="72d91-104">擷取列舉開頭的呼叫中的下一個屬性[BeginEnumeration](beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="72d91-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="72d91-105">語法</span><span class="sxs-lookup"><span data-stu-id="72d91-105">Syntax</span></span>  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a><span data-ttu-id="72d91-106">參數</span><span class="sxs-lookup"><span data-stu-id="72d91-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="72d91-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="72d91-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="72d91-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="72d91-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="72d91-109">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="72d91-109">[in] Reserved.</span></span> <span data-ttu-id="72d91-110">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="72d91-110">This parameter must be 0.</span></span>

`pstrName`  
<span data-ttu-id="72d91-111">[out]新`BSTR`，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="72d91-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="72d91-112">您可以將此參數設定為`null`如果不需要名稱。</span><span class="sxs-lookup"><span data-stu-id="72d91-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`  
<span data-ttu-id="72d91-113">[out]A`VARIANT`填入屬性的值。</span><span class="sxs-lookup"><span data-stu-id="72d91-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="72d91-114">您可以將此參數設定為`null`如果不需要值。</span><span class="sxs-lookup"><span data-stu-id="72d91-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="72d91-115">如果函數傳回的錯誤碼，`VARIANT`傳遞至`pVal`左未經修改。</span><span class="sxs-lookup"><span data-stu-id="72d91-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span> 

`pvtType`  
<span data-ttu-id="72d91-116">[out]指標`CIMTYPE`變數 (`LONG`屬性的型別會放入)。</span><span class="sxs-lookup"><span data-stu-id="72d91-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="72d91-117">這個屬性的值可以是`VT_NULL_VARIANT`，在此情況下則需要判斷實際屬性型別。</span><span class="sxs-lookup"><span data-stu-id="72d91-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="72d91-118">這個參數也可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="72d91-118">This parameter can also be `null`.</span></span> 

`plFlavor`  
<span data-ttu-id="72d91-119">[out]`null`，或接收資訊來源之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="72d91-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="72d91-120">請參閱 [備註] 提供可能的值。</span><span class="sxs-lookup"><span data-stu-id="72d91-120">See the [Remarks] section for possible values.</span></span> 

## <a name="return-value"></a><span data-ttu-id="72d91-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="72d91-121">Return value</span></span>

<span data-ttu-id="72d91-122">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="72d91-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="72d91-123">常數</span><span class="sxs-lookup"><span data-stu-id="72d91-123">Constant</span></span>  |<span data-ttu-id="72d91-124">值</span><span class="sxs-lookup"><span data-stu-id="72d91-124">Value</span></span>  |<span data-ttu-id="72d91-125">描述</span><span class="sxs-lookup"><span data-stu-id="72d91-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="72d91-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="72d91-126">0x80041001</span></span> | <span data-ttu-id="72d91-127">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="72d91-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="72d91-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="72d91-128">0x80041008</span></span> | <span data-ttu-id="72d91-129">參數無效。</span><span class="sxs-lookup"><span data-stu-id="72d91-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="72d91-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="72d91-130">0x8004101d</span></span> | <span data-ttu-id="72d91-131">沒有不需要呼叫[ `BeginEnumeration` ](beginenumeration.md)函式。</span><span class="sxs-lookup"><span data-stu-id="72d91-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="72d91-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="72d91-132">0x80041006</span></span> | <span data-ttu-id="72d91-133">使用開始新的列舉型別沒有足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="72d91-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="72d91-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="72d91-134">0x80041015</span></span> | <span data-ttu-id="72d91-135">遠端程序呼叫之目前處理序和失敗的 Windows 管理。</span><span class="sxs-lookup"><span data-stu-id="72d91-135">The remote procedure call betweeen the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="72d91-136">0</span><span class="sxs-lookup"><span data-stu-id="72d91-136">0</span></span> | <span data-ttu-id="72d91-137">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="72d91-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="72d91-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="72d91-138">0x40005</span></span> | <span data-ttu-id="72d91-139">列舉中沒有其他內容。</span><span class="sxs-lookup"><span data-stu-id="72d91-139">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="72d91-140">備註</span><span class="sxs-lookup"><span data-stu-id="72d91-140">Remarks</span></span>

<span data-ttu-id="72d91-141">此函式會包裝呼叫[IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="72d91-141">This function wraps a call to the [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="72d91-142">這個方法也會傳回系統屬性。</span><span class="sxs-lookup"><span data-stu-id="72d91-142">This method also returns system properties.</span></span>

<span data-ttu-id="72d91-143">如果屬性的基礎類型的物件路徑、 日期或時間或另一種特殊類型，則傳回的類型不包含足夠的資訊。</span><span class="sxs-lookup"><span data-stu-id="72d91-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="72d91-144">呼叫端必須檢查`CIMTYPE`指定判斷屬性是否為物件參考、 日期或時間或另一種特殊類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="72d91-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="72d91-145">如果`plFlavor`不`null`、`LONG`值接收資訊屬性的原點，如下所示：</span><span class="sxs-lookup"><span data-stu-id="72d91-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="72d91-146">常數</span><span class="sxs-lookup"><span data-stu-id="72d91-146">Constant</span></span>  |<span data-ttu-id="72d91-147">值</span><span class="sxs-lookup"><span data-stu-id="72d91-147">Value</span></span>  |<span data-ttu-id="72d91-148">描述</span><span class="sxs-lookup"><span data-stu-id="72d91-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="72d91-149">0x40</span><span class="sxs-lookup"><span data-stu-id="72d91-149">0x40</span></span> | <span data-ttu-id="72d91-150">屬性是標準的系統屬性。</span><span class="sxs-lookup"><span data-stu-id="72d91-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="72d91-151">0x20</span><span class="sxs-lookup"><span data-stu-id="72d91-151">0x20</span></span> | <span data-ttu-id="72d91-152">類別： 屬性繼承自父類別。</span><span class="sxs-lookup"><span data-stu-id="72d91-152">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="72d91-153">執行個體： 屬性繼承自父類別，而尚未修改的執行個體。</span><span class="sxs-lookup"><span data-stu-id="72d91-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="72d91-154">0</span><span class="sxs-lookup"><span data-stu-id="72d91-154">0</span></span> | <span data-ttu-id="72d91-155">類別： 屬性屬於衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="72d91-155">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="72d91-156">執行個體： 執行個體; 所修改的屬性也就是所提供的值，或辨識符號的加入或修改。</span><span class="sxs-lookup"><span data-stu-id="72d91-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="72d91-157">需求</span><span class="sxs-lookup"><span data-stu-id="72d91-157">Requirements</span></span>  
 <span data-ttu-id="72d91-158">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72d91-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72d91-159">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="72d91-159">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="72d91-160">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="72d91-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d91-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72d91-161">See also</span></span>  
[<span data-ttu-id="72d91-162">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="72d91-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
