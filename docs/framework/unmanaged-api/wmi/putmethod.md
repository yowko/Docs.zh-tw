---
title: "PutMethod 函式 （Unmanaged API 參考）"
description: "PutMethod 函式建立的方法。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutMethod
helpviewer_keywords: PutMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64e43165b34b74540931b308100c9ca942946bcf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="putmethod-function"></a><span data-ttu-id="85684-103">PutMethod 函式</span><span class="sxs-lookup"><span data-stu-id="85684-103">PutMethod function</span></span>
<span data-ttu-id="85684-104">建立方法。</span><span class="sxs-lookup"><span data-stu-id="85684-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="85684-105">語法</span><span class="sxs-lookup"><span data-stu-id="85684-105">Syntax</span></span>  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="85684-106">參數</span><span class="sxs-lookup"><span data-stu-id="85684-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="85684-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="85684-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="85684-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="85684-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="85684-109">[in]若要建立方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="85684-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="85684-110">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="85684-110">[in] Reserved.</span></span> <span data-ttu-id="85684-111">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="85684-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="85684-112">[in]指標，一份[__Parameters 系統類別](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)包含`in`方法的參數。</span><span class="sxs-lookup"><span data-stu-id="85684-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="85684-113">如果，則會忽略這個參數設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="85684-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="85684-114">[in] 指標，一份[__Parameters 系統類別](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)包含`out`方法的參數。</span><span class="sxs-lookup"><span data-stu-id="85684-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="85684-115">如果，則會忽略這個參數設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="85684-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="85684-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="85684-116">Return value</span></span>

<span data-ttu-id="85684-117">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="85684-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="85684-118">常數</span><span class="sxs-lookup"><span data-stu-id="85684-118">Constant</span></span>  |<span data-ttu-id="85684-119">值</span><span class="sxs-lookup"><span data-stu-id="85684-119">Value</span></span>  |<span data-ttu-id="85684-120">說明</span><span class="sxs-lookup"><span data-stu-id="85684-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="85684-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="85684-121">0x80041008</span></span> | <span data-ttu-id="85684-122">一或多個參數都不是有效的。</span><span class="sxs-lookup"><span data-stu-id="85684-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="85684-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="85684-123">0x80041043</span></span> | <span data-ttu-id="85684-124">`[in, out]`方法參數中指定*pInSignature*和*pOutSignature*物件具有不同的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="85684-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="85684-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="85684-125">0x80041036</span></span> | <span data-ttu-id="85684-126">方法參數遺漏的規格**識別碼**限定詞。</span><span class="sxs-lookup"><span data-stu-id="85684-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="85684-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="85684-127">0x80041038</span></span> | <span data-ttu-id="85684-128">指派給方法參數的識別碼數列不連續或沒有不會從 0 開始。</span><span class="sxs-lookup"><span data-stu-id="85684-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="85684-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="85684-129">0x80041039</span></span> | <span data-ttu-id="85684-130">方法的傳回值具有**識別碼**限定詞。</span><span class="sxs-lookup"><span data-stu-id="85684-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="85684-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="85684-131">0x80041034</span></span> | <span data-ttu-id="85684-132">嘗試將重複使用現有的方法名稱自父類別，並且簽章不符。</span><span class="sxs-lookup"><span data-stu-id="85684-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="85684-133">0</span><span class="sxs-lookup"><span data-stu-id="85684-133">0</span></span> | <span data-ttu-id="85684-134">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="85684-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="85684-135">備註</span><span class="sxs-lookup"><span data-stu-id="85684-135">Remarks</span></span>

<span data-ttu-id="85684-136">此函式會包裝呼叫[IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="85684-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="85684-137">這個方法呼叫時才支援`ptr`為 CIM 類別定義。</span><span class="sxs-lookup"><span data-stu-id="85684-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="85684-138">方法操作中未提供[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)指向 CIM 執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="85684-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="85684-139">使用者無法建立方法以底線開頭或結尾的名稱。</span><span class="sxs-lookup"><span data-stu-id="85684-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="85684-140">這被保留給系統的類別和屬性。</span><span class="sxs-lookup"><span data-stu-id="85684-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="85684-141">一種方法，如`in`和`out`參數說明中做為屬性[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)物件。</span><span class="sxs-lookup"><span data-stu-id="85684-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="85684-142">`[in/out]`參數可由相同的屬性加入至這兩個所指向的物件定義`pInSignature`和`pOutSignature`參數。</span><span class="sxs-lookup"><span data-stu-id="85684-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="85684-143">在此情況下，內容會共用相同**識別碼**辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="85684-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="85684-144">中的每一個屬性[__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)以外類別物件`ReturnValue`必須**識別碼**辨識符號，以零為起始的數字值，識別這些參數會顯示的順序。</span><span class="sxs-lookup"><span data-stu-id="85684-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="85684-145">任何兩個參數可以具有相同**識別碼**值，且沒有**識別碼**略過的值。</span><span class="sxs-lookup"><span data-stu-id="85684-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="85684-146">如果發生其中一個條件，`PutMethod`函式會傳回`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`。</span><span class="sxs-lookup"><span data-stu-id="85684-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="85684-147">範例</span><span class="sxs-lookup"><span data-stu-id="85684-147">Example</span></span>

<span data-ttu-id="85684-148">如需範例，請參閱[IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="85684-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="85684-149">需求</span><span class="sxs-lookup"><span data-stu-id="85684-149">Requirements</span></span>  
 <span data-ttu-id="85684-150">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85684-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85684-151">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="85684-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="85684-152">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="85684-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85684-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="85684-153">See also</span></span>  
[<span data-ttu-id="85684-154">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="85684-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
