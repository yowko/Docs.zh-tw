---
title: "PutInstanceWmi 函式 （Unmanaged API 參考）"
description: "PutInstanceWmi 函式會建立或更新現有類別的執行個體。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7a4ffce4789fb59d84778d02b41910c974216bd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="49fc1-103">PutInstanceWmi 函式</span><span class="sxs-lookup"><span data-stu-id="49fc1-103">PutInstanceWmi function</span></span>
<span data-ttu-id="49fc1-104">建立或更新現有類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="49fc1-105">WMI 存放庫會寫入執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="49fc1-106">語法</span><span class="sxs-lookup"><span data-stu-id="49fc1-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="49fc1-107">參數</span><span class="sxs-lookup"><span data-stu-id="49fc1-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="49fc1-108">[in]要寫入的執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="49fc1-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="49fc1-109">[in]影響此函式的行為的旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="49fc1-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="49fc1-110">下列的值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="49fc1-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="49fc1-111">常數</span><span class="sxs-lookup"><span data-stu-id="49fc1-111">Constant</span></span>  |<span data-ttu-id="49fc1-112">值</span><span class="sxs-lookup"><span data-stu-id="49fc1-112">Value</span></span>  |<span data-ttu-id="49fc1-113">說明</span><span class="sxs-lookup"><span data-stu-id="49fc1-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="49fc1-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="49fc1-114">0x20000</span></span> | <span data-ttu-id="49fc1-115">如果設定，WMI 不會儲存任何限定詞與**Amended**類別。</span><span class="sxs-lookup"><span data-stu-id="49fc1-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="49fc1-116">如果未設定，它會假設，此物件不會進行當地語系化，且所有限定詞 storedwith 這個執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="49fc1-117">0</span><span class="sxs-lookup"><span data-stu-id="49fc1-117">0</span></span> | <span data-ttu-id="49fc1-118">如果不存在，或是覆寫它，如果它已經存在，請建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="49fc1-119">1</span><span class="sxs-lookup"><span data-stu-id="49fc1-119">1</span></span> | <span data-ttu-id="49fc1-120">更新執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-120">Update the instance.</span></span> <span data-ttu-id="49fc1-121">若要成功呼叫必須存在之執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="49fc1-122">2</span><span class="sxs-lookup"><span data-stu-id="49fc1-122">2</span></span> | <span data-ttu-id="49fc1-123">建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-123">Create the instance.</span></span> <span data-ttu-id="49fc1-124">如果已經有該執行個體，呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="49fc1-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="49fc1-125">0x10</span><span class="sxs-lookup"><span data-stu-id="49fc1-125">0x10</span></span> | <span data-ttu-id="49fc1-126">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="49fc1-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="49fc1-127">[in]一般而言，這個值是`null`。</span><span class="sxs-lookup"><span data-stu-id="49fc1-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="49fc1-128">否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可用的提供者所提供的要求的類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-128">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="49fc1-129">[out]如果`null`，不使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="49fc1-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="49fc1-130">如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY`，函式立即傳回且`WBEM_S_NO_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="49fc1-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="49fc1-131">`ppCallResult`參數接收新的指標[IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx)物件。</span><span class="sxs-lookup"><span data-stu-id="49fc1-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="49fc1-132">傳回值</span><span class="sxs-lookup"><span data-stu-id="49fc1-132">Return value</span></span>

<span data-ttu-id="49fc1-133">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="49fc1-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="49fc1-134">常數</span><span class="sxs-lookup"><span data-stu-id="49fc1-134">Constant</span></span>  |<span data-ttu-id="49fc1-135">值</span><span class="sxs-lookup"><span data-stu-id="49fc1-135">Value</span></span>  |<span data-ttu-id="49fc1-136">說明</span><span class="sxs-lookup"><span data-stu-id="49fc1-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="49fc1-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="49fc1-137">0x80041003</span></span> | <span data-ttu-id="49fc1-138">使用者沒有權限來更新指定類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="49fc1-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="49fc1-139">0x80041001</span></span> | <span data-ttu-id="49fc1-140">發生意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="49fc1-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="49fc1-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="49fc1-141">0x80041010</span></span> | <span data-ttu-id="49fc1-142">支援這個執行個體的類別無效。</span><span class="sxs-lookup"><span data-stu-id="49fc1-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="49fc1-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="49fc1-143">0x80041028</span></span> | <span data-ttu-id="49fc1-144">`null`屬性不能指定`null`，例如，標示**索引**或**Not_Null**限定詞。</span><span class="sxs-lookup"><span data-stu-id="49fc1-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="49fc1-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="49fc1-145">0x8004100f</span></span> | <span data-ttu-id="49fc1-146">指定的執行個體不是有效的。</span><span class="sxs-lookup"><span data-stu-id="49fc1-146">The specified instance is not valid.</span></span> <span data-ttu-id="49fc1-147">(例如，呼叫`PutInstanceWmi`類別會傳回此值。)</span><span class="sxs-lookup"><span data-stu-id="49fc1-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="49fc1-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="49fc1-148">0x80041008</span></span> | <span data-ttu-id="49fc1-149">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="49fc1-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="49fc1-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="49fc1-150">0x80041019</span></span> | <span data-ttu-id="49fc1-151">`WBEM_FLAG_CREATE_ONLY`指定的旗標，但執行個體已經存在。</span><span class="sxs-lookup"><span data-stu-id="49fc1-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="49fc1-152">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="49fc1-152">0x80041002</span></span> | <span data-ttu-id="49fc1-153">`WBEM_FLAG_UPDATE_ONLY`中指定了`lFlags`，但執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="49fc1-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="49fc1-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="49fc1-154">0x80041006</span></span> | <span data-ttu-id="49fc1-155">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="49fc1-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="49fc1-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="49fc1-156">0x80041033</span></span> | <span data-ttu-id="49fc1-157">WMI 是可能已停止和重新啟動。</span><span class="sxs-lookup"><span data-stu-id="49fc1-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="49fc1-158">呼叫[ConnectServerWmi](connectserverwmi.md)一次。</span><span class="sxs-lookup"><span data-stu-id="49fc1-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="49fc1-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="49fc1-159">0x80041015</span></span> | <span data-ttu-id="49fc1-160">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="49fc1-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="49fc1-161">0</span><span class="sxs-lookup"><span data-stu-id="49fc1-161">0</span></span> | <span data-ttu-id="49fc1-162">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="49fc1-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="49fc1-163">備註</span><span class="sxs-lookup"><span data-stu-id="49fc1-163">Remarks</span></span>

<span data-ttu-id="49fc1-164">此函式會包裝呼叫[IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="49fc1-164">This function wraps a call to the [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="49fc1-165">`PutInstanceWmi`函式建立執行個體，並更新現有的類別的執行個體的支援。</span><span class="sxs-lookup"><span data-stu-id="49fc1-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="49fc1-166">如何根據`pCtx`設定參數時，部分或所有執行個體的屬性會更新。</span><span class="sxs-lookup"><span data-stu-id="49fc1-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="49fc1-167">當執行個體所指`pInst`屬於 Windows 管理子類別，呼叫的所有提供者負責從子類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="49fc1-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="49fc1-168">所有這些提供者必須原始成功`PutInstanceWmi`要求才能成功。</span><span class="sxs-lookup"><span data-stu-id="49fc1-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="49fc1-169">支援的最上層的類別階層架構中的提供者會呼叫第一次。</span><span class="sxs-lookup"><span data-stu-id="49fc1-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="49fc1-170">按呼叫順序會繼續進行的最上層類別的子類別，然後從上到下直到 Windows 管理到達的提供者擁有所指向的執行個體的類別`pInst`。</span><span class="sxs-lookup"><span data-stu-id="49fc1-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="49fc1-171">Windows 管理未呼叫提供者的任何子類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="49fc1-172">當應用程式必須更新所屬的類別階層架構中，執行個體`pInst`參數必須指向包含要修改之屬性的執行個體。</span><span class="sxs-lookup"><span data-stu-id="49fc1-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="49fc1-173">也就是說，請考慮目標執行個體屬於**ClassB**。</span><span class="sxs-lookup"><span data-stu-id="49fc1-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="49fc1-174">**ClassB**執行個體是衍生自**ClassA**，和**ClassA**定義屬性**PropA**。</span><span class="sxs-lookup"><span data-stu-id="49fc1-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="49fc1-175">如果應用程式就會想要變更的值**PropA**中**ClassB**執行個體，它必須設定`pInst`該執行個體，而不是執行個體**ClassA**.</span><span class="sxs-lookup"><span data-stu-id="49fc1-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="49fc1-176">呼叫`PutInstanceWmi`不允許抽象類別的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="49fc1-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="49fc1-177">如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="49fc1-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="49fc1-178">需求</span><span class="sxs-lookup"><span data-stu-id="49fc1-178">Requirements</span></span>  
 <span data-ttu-id="49fc1-179">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49fc1-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49fc1-180">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="49fc1-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="49fc1-181">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="49fc1-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49fc1-182">請參閱</span><span class="sxs-lookup"><span data-stu-id="49fc1-182">See also</span></span>  
[<span data-ttu-id="49fc1-183">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="49fc1-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
