---
title: PutMethod 函式（非受控 API 參考）
description: PutMethod 函數會建立方法。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b41cbbade9da5c2095309b9039b8ce2758f6f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798359"
---
# <a name="putmethod-function"></a><span data-ttu-id="3188a-103">PutMethod 函式</span><span class="sxs-lookup"><span data-stu-id="3188a-103">PutMethod function</span></span>
<span data-ttu-id="3188a-104">建立方法。</span><span class="sxs-lookup"><span data-stu-id="3188a-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="3188a-105">語法</span><span class="sxs-lookup"><span data-stu-id="3188a-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="3188a-106">參數</span><span class="sxs-lookup"><span data-stu-id="3188a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3188a-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="3188a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3188a-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="3188a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="3188a-109">在要建立之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="3188a-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="3188a-110">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="3188a-110">[in] Reserved.</span></span> <span data-ttu-id="3188a-111">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="3188a-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="3188a-112">在[__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters)複本的指標，其中包含`in`方法的參數。</span><span class="sxs-lookup"><span data-stu-id="3188a-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="3188a-113">如果設定為`null`，則會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="3188a-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="3188a-114">在 [__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters)複本的指標，其中包含`out`方法的參數。</span><span class="sxs-lookup"><span data-stu-id="3188a-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="3188a-115">如果設定為`null`，則會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="3188a-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="3188a-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="3188a-116">Return value</span></span>

<span data-ttu-id="3188a-117">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="3188a-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3188a-118">常數</span><span class="sxs-lookup"><span data-stu-id="3188a-118">Constant</span></span>  |<span data-ttu-id="3188a-119">值</span><span class="sxs-lookup"><span data-stu-id="3188a-119">Value</span></span>  |<span data-ttu-id="3188a-120">描述</span><span class="sxs-lookup"><span data-stu-id="3188a-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3188a-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3188a-121">0x80041008</span></span> | <span data-ttu-id="3188a-122">一或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="3188a-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="3188a-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="3188a-123">0x80041043</span></span> | <span data-ttu-id="3188a-124">PInSignature `[in, out]`和*pOutSignature*物件中指定的方法參數具有不同的限定詞。</span><span class="sxs-lookup"><span data-stu-id="3188a-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="3188a-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="3188a-125">0x80041036</span></span> | <span data-ttu-id="3188a-126">方法參數缺少**識別碼**辨識符號的規格。</span><span class="sxs-lookup"><span data-stu-id="3188a-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="3188a-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="3188a-127">0x80041038</span></span> | <span data-ttu-id="3188a-128">指派給方法參數的識別碼系列不是連續的，也不是從0開始。</span><span class="sxs-lookup"><span data-stu-id="3188a-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="3188a-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="3188a-129">0x80041039</span></span> | <span data-ttu-id="3188a-130">方法的傳回值具有**識別碼**辨識符號。</span><span class="sxs-lookup"><span data-stu-id="3188a-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="3188a-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="3188a-131">0x80041034</span></span> | <span data-ttu-id="3188a-132">嘗試重複使用父類別中現有的方法名稱，而且簽章不相符。</span><span class="sxs-lookup"><span data-stu-id="3188a-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="3188a-133">0</span><span class="sxs-lookup"><span data-stu-id="3188a-133">0</span></span> | <span data-ttu-id="3188a-134">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3188a-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="3188a-135">備註</span><span class="sxs-lookup"><span data-stu-id="3188a-135">Remarks</span></span>

<span data-ttu-id="3188a-136">此函式會包裝對[IWbemClassObject：:P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3188a-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="3188a-137">只有當`ptr`是 CIM 類別定義時，才支援這個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="3188a-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="3188a-138">方法操作無法從指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標使用。</span><span class="sxs-lookup"><span data-stu-id="3188a-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="3188a-139">使用者無法建立名稱以底線開頭或結尾的方法。</span><span class="sxs-lookup"><span data-stu-id="3188a-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="3188a-140">這會保留給系統類別和屬性。</span><span class="sxs-lookup"><span data-stu-id="3188a-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="3188a-141">針對方法，和`in` `out`參數會描述為[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)物件中的屬性。</span><span class="sxs-lookup"><span data-stu-id="3188a-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="3188a-142">您可以將相同的屬性新增至和`pOutSignature`參數所`pInSignature`指向的兩個物件，藉以定義參數。`[in/out]`</span><span class="sxs-lookup"><span data-stu-id="3188a-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="3188a-143">在此情況下，屬性會共用相同的**識別碼**辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="3188a-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="3188a-144">以外的[__Parameters](/windows/desktop/WmiSdk/--parameters)類別物件`ReturnValue`中的每個屬性都必須具有**識別碼**辨識符號，這是以零為基底的數值，可識別參數出現的順序。</span><span class="sxs-lookup"><span data-stu-id="3188a-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="3188a-145">任何兩個參數都不能有相同的**識別碼**值，也無法略過任何**識別碼**值。</span><span class="sxs-lookup"><span data-stu-id="3188a-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="3188a-146">如果發生任一種狀況， `PutMethod`此`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`函式會傳回。</span><span class="sxs-lookup"><span data-stu-id="3188a-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="3188a-147">範例</span><span class="sxs-lookup"><span data-stu-id="3188a-147">Example</span></span>

<span data-ttu-id="3188a-148">如需範例，請參閱[IWbemClassObject：:P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)方法。</span><span class="sxs-lookup"><span data-stu-id="3188a-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3188a-149">需求</span><span class="sxs-lookup"><span data-stu-id="3188a-149">Requirements</span></span>  
 <span data-ttu-id="3188a-150">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3188a-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3188a-151">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3188a-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3188a-152">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3188a-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3188a-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3188a-153">See also</span></span>

- [<span data-ttu-id="3188a-154">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="3188a-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
