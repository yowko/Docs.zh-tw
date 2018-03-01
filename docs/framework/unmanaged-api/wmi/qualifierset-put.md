---
title: "QualifierSet_Put 函式 （Unmanaged API 參考）"
description: "QualifierSet_Put 函式會寫入具名的辨識符號和它的值。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bf5c6dbf0f707942d58f4d7cf155636f0532724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="32221-103">QualifierSet_Put 函式</span><span class="sxs-lookup"><span data-stu-id="32221-103">QualifierSet_Put function</span></span>
<span data-ttu-id="32221-104">寫入具名的辨識符號和值。</span><span class="sxs-lookup"><span data-stu-id="32221-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="32221-105">新限定詞會覆寫先前同名的值。</span><span class="sxs-lookup"><span data-stu-id="32221-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="32221-106">如果不存在限定詞，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="32221-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="32221-107">語法</span><span class="sxs-lookup"><span data-stu-id="32221-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="32221-108">參數</span><span class="sxs-lookup"><span data-stu-id="32221-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="32221-109">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="32221-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="32221-110">[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="32221-110">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="32221-111">[in]要寫入的限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="32221-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="32221-112">`pVal`[in]有效的指標`VARIANT`，其中包含要寫入的限定詞。</span><span class="sxs-lookup"><span data-stu-id="32221-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="32221-113">此參數不得為`null`。</span><span class="sxs-lookup"><span data-stu-id="32221-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="32221-114">`lFlavor`[in]下列常數，定義所需的限定詞標註，這個辨識符號的其中一個。</span><span class="sxs-lookup"><span data-stu-id="32221-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="32221-115">預設值是`WBEM_FLAVOR_OVERRIDABLE`(0)。</span><span class="sxs-lookup"><span data-stu-id="32221-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="32221-116">常數</span><span class="sxs-lookup"><span data-stu-id="32221-116">Constant</span></span>  |<span data-ttu-id="32221-117">值</span><span class="sxs-lookup"><span data-stu-id="32221-117">Value</span></span>  |<span data-ttu-id="32221-118">描述</span><span class="sxs-lookup"><span data-stu-id="32221-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="32221-119">0</span><span class="sxs-lookup"><span data-stu-id="32221-119">0</span></span> | <span data-ttu-id="32221-120">限定詞會覆寫衍生的類別或執行個體中。</span><span class="sxs-lookup"><span data-stu-id="32221-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="32221-121">**這是預設值。**</span><span class="sxs-lookup"><span data-stu-id="32221-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="32221-122">1</span><span class="sxs-lookup"><span data-stu-id="32221-122">1</span></span> | <span data-ttu-id="32221-123">限定詞會傳播到執行個體。</span><span class="sxs-lookup"><span data-stu-id="32221-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="32221-124">2</span><span class="sxs-lookup"><span data-stu-id="32221-124">2</span></span> | <span data-ttu-id="32221-125">限定詞會傳播到衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="32221-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="32221-126">' WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="32221-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="32221-127">0x10</span><span class="sxs-lookup"><span data-stu-id="32221-127">0x10</span></span> | <span data-ttu-id="32221-128">無法在衍生類別或執行個體中覆寫限定詞。</span><span class="sxs-lookup"><span data-stu-id="32221-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="32221-129">' WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="32221-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="32221-130">0x80</span><span class="sxs-lookup"><span data-stu-id="32221-130">0x80</span></span> | <span data-ttu-id="32221-131">限定詞已經過當地語系化。</span><span class="sxs-lookup"><span data-stu-id="32221-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="32221-132">傳回值</span><span class="sxs-lookup"><span data-stu-id="32221-132">Return value</span></span>

<span data-ttu-id="32221-133">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="32221-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="32221-134">常數</span><span class="sxs-lookup"><span data-stu-id="32221-134">Constant</span></span>  |<span data-ttu-id="32221-135">值</span><span class="sxs-lookup"><span data-stu-id="32221-135">Value</span></span>  |<span data-ttu-id="32221-136">描述</span><span class="sxs-lookup"><span data-stu-id="32221-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="32221-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="32221-137">0x8004101f</span></span> | <span data-ttu-id="32221-138">曾不合法嘗試指定**金鑰**不得為索引鍵屬性上的限定詞。</span><span class="sxs-lookup"><span data-stu-id="32221-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="32221-139">指定索引鍵 om c，則為物件的協助定義，且無法變更針對每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="32221-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="32221-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="32221-140">0x80041008</span></span> | <span data-ttu-id="32221-141">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="32221-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="32221-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="32221-142">0x80041029</span></span> | <span data-ttu-id="32221-143">`pVal`參數不是合法的限定詞類型。</span><span class="sxs-lookup"><span data-stu-id="32221-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="32221-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="32221-144">0x8004101a</span></span> | <span data-ttu-id="32221-145">不可能呼叫`QualifierSet_Put`限定詞的方法，因為主控物件不允許覆寫。</span><span class="sxs-lookup"><span data-stu-id="32221-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="32221-146">0</span><span class="sxs-lookup"><span data-stu-id="32221-146">0</span></span> | <span data-ttu-id="32221-147">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="32221-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="32221-148">備註</span><span class="sxs-lookup"><span data-stu-id="32221-148">Remarks</span></span>

<span data-ttu-id="32221-149">此函式會包裝呼叫[IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="32221-149">This function wraps a call to the [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="32221-150">需求</span><span class="sxs-lookup"><span data-stu-id="32221-150">Requirements</span></span>  
 <span data-ttu-id="32221-151">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32221-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32221-152">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="32221-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="32221-153">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32221-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32221-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32221-154">See also</span></span>  
[<span data-ttu-id="32221-155">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="32221-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
