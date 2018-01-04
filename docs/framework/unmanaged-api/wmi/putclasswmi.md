---
title: "PutClassWmi 函式 （Unmanaged API 參考）"
description: "PutClassWmi 函式會建立新的類別或更新現有。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 219cec2096cd3d1dfe1e0d3c0903b62692e444e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="putclasswmi-function"></a><span data-ttu-id="42211-103">PutClassWmi 函式</span><span class="sxs-lookup"><span data-stu-id="42211-103">PutClassWmi function</span></span>
<span data-ttu-id="42211-104">建立新的類別或更新現有。</span><span class="sxs-lookup"><span data-stu-id="42211-104">Creates a new class or updates an existing one.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="42211-105">語法</span><span class="sxs-lookup"><span data-stu-id="42211-105">Syntax</span></span>  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="42211-106">參數</span><span class="sxs-lookup"><span data-stu-id="42211-106">Parameters</span></span>

`pObject`    
<span data-ttu-id="42211-107">[in]有效的類別定義的指標。</span><span class="sxs-lookup"><span data-stu-id="42211-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="42211-108">它必須正確地初始化的所有必要的屬性值。</span><span class="sxs-lookup"><span data-stu-id="42211-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`   
<span data-ttu-id="42211-109">[in]影響此函式的行為的旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="42211-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="42211-110">下列的值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="42211-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="42211-111">常數</span><span class="sxs-lookup"><span data-stu-id="42211-111">Constant</span></span>  |<span data-ttu-id="42211-112">值</span><span class="sxs-lookup"><span data-stu-id="42211-112">Value</span></span>  |<span data-ttu-id="42211-113">描述</span><span class="sxs-lookup"><span data-stu-id="42211-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="42211-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="42211-114">0x20000</span></span> | <span data-ttu-id="42211-115">如果 WMI 集不會儲存任何限定詞與修改過的類別。</span><span class="sxs-lookup"><span data-stu-id="42211-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> </br> <span data-ttu-id="42211-116">如果未設定，它會假設，此物件不會進行當地語系化，且所有限定詞 storedwith 這個執行個體。</span><span class="sxs-lookup"><span data-stu-id="42211-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="42211-117">0</span><span class="sxs-lookup"><span data-stu-id="42211-117">0</span></span> | <span data-ttu-id="42211-118">如果不存在，或是覆寫它，如果它已經存在，請建立類別。</span><span class="sxs-lookup"><span data-stu-id="42211-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="42211-119">1</span><span class="sxs-lookup"><span data-stu-id="42211-119">1</span></span> | <span data-ttu-id="42211-120">更新類別。</span><span class="sxs-lookup"><span data-stu-id="42211-120">Update the class.</span></span> <span data-ttu-id="42211-121">若要成功呼叫必須存在類別。</span><span class="sxs-lookup"><span data-stu-id="42211-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="42211-122">2</span><span class="sxs-lookup"><span data-stu-id="42211-122">2</span></span> | <span data-ttu-id="42211-123">建立類別。</span><span class="sxs-lookup"><span data-stu-id="42211-123">Create the class.</span></span> <span data-ttu-id="42211-124">如果類別已存在，則呼叫會失敗。</span><span class="sxs-lookup"><span data-stu-id="42211-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="42211-125">0x10</span><span class="sxs-lookup"><span data-stu-id="42211-125">0x10</span></span> | <span data-ttu-id="42211-126">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="42211-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="42211-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="42211-127">0x10000</span></span> | <span data-ttu-id="42211-128">推入提供者在呼叫時，必須指定這個旗標`PutClassWmi`，指出這個類別已變更。</span><span class="sxs-lookup"><span data-stu-id="42211-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="42211-129">0</span><span class="sxs-lookup"><span data-stu-id="42211-129">0</span></span> | <span data-ttu-id="42211-130">允許更新，如果有任何衍生的類別和類別的任何執行個體類別。</span><span class="sxs-lookup"><span data-stu-id="42211-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="42211-131">它也可讓更新在所有情況下如果只是變更並不重要的辨識符號，例如描述限定詞。</span><span class="sxs-lookup"><span data-stu-id="42211-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="42211-132">如果類別具有執行個體或變更重要的限定詞，則更新失敗。</span><span class="sxs-lookup"><span data-stu-id="42211-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="42211-133">0x20</span><span class="sxs-lookup"><span data-stu-id="42211-133">0x20</span></span> | <span data-ttu-id="42211-134">即使有子類別，只要變更不會發生任何衝突造成與子類別，可讓更新類別。</span><span class="sxs-lookup"><span data-stu-id="42211-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="42211-135">例如，此旗標會允許新屬性加入至先前未提及的任何子類別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="42211-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="42211-136">如果類別的執行個體，則更新失敗。</span><span class="sxs-lookup"><span data-stu-id="42211-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="42211-137">0x40</span><span class="sxs-lookup"><span data-stu-id="42211-137">0x40</span></span> | <span data-ttu-id="42211-138">衝突的子類別存在時，會強制更新類別。</span><span class="sxs-lookup"><span data-stu-id="42211-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="42211-139">例如，這個旗標會強制更新有類別限定詞定義在子類別，而基底類別會嘗試將相同的辨識符號與修改現有的其中一個成員互相衝突。</span><span class="sxs-lookup"><span data-stu-id="42211-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with thte existing one.</span></span> <span data-ttu-id="42211-140">強制模式中 tis 衝突的解決方式刪除衝突的辨識符號中的子類別。</span><span class="sxs-lookup"><span data-stu-id="42211-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`  
<span data-ttu-id="42211-141">[in]一般而言，這個值是`null`。</span><span class="sxs-lookup"><span data-stu-id="42211-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="42211-142">否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可用的提供者所提供的要求的類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42211-142">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="42211-143">[out]如果`null`，不使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="42211-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="42211-144">如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY`，函式立即傳回且`WBEM_S_NO_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="42211-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="42211-145">`ppCallResult`參數接收新的指標[IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx)物件。</span><span class="sxs-lookup"><span data-stu-id="42211-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="42211-146">傳回值</span><span class="sxs-lookup"><span data-stu-id="42211-146">Return value</span></span>

<span data-ttu-id="42211-147">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="42211-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="42211-148">常數</span><span class="sxs-lookup"><span data-stu-id="42211-148">Constant</span></span>  |<span data-ttu-id="42211-149">值</span><span class="sxs-lookup"><span data-stu-id="42211-149">Value</span></span>  |<span data-ttu-id="42211-150">描述</span><span class="sxs-lookup"><span data-stu-id="42211-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="42211-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="42211-151">0x80041003</span></span> | <span data-ttu-id="42211-152">使用者沒有建立或修改的類別權限。</span><span class="sxs-lookup"><span data-stu-id="42211-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="42211-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="42211-153">0x80041001</span></span> | <span data-ttu-id="42211-154">發生意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="42211-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="42211-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="42211-155">0x80041010</span></span> | <span data-ttu-id="42211-156">指定的類別不是有效的。</span><span class="sxs-lookup"><span data-stu-id="42211-156">The specified class is not valid.</span></span> <span data-ttu-id="42211-157">一般而言，這表示`pObject`指定執行個體物件。</span><span class="sxs-lookup"><span data-stu-id="42211-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="42211-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="42211-158">0x80041008</span></span> | <span data-ttu-id="42211-159">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="42211-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="42211-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="42211-160">0x80041016</span></span> | <span data-ttu-id="42211-161">指定的類別名稱無效。</span><span class="sxs-lookup"><span data-stu-id="42211-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="42211-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="42211-162">0x80041025</span></span> | <span data-ttu-id="42211-163">您嘗試進行的變更，可能會導致子類別失效。</span><span class="sxs-lookup"><span data-stu-id="42211-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="42211-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="42211-164">0x80041019</span></span> | <span data-ttu-id="42211-165">`WBEM_FLAG_CREATE_ONLY`指定旗標，但類別已存在。</span><span class="sxs-lookup"><span data-stu-id="42211-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="42211-166">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="42211-166">0x80041002</span></span> | <span data-ttu-id="42211-167">`WBEM_FLAG_UPDATE_ONLY`中指定了`lFlags`，而且找不到類別。</span><span class="sxs-lookup"><span data-stu-id="42211-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="42211-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="42211-168">0x80041020</span></span> | <span data-ttu-id="42211-169">類別所需的屬性不是所有尚未設定。</span><span class="sxs-lookup"><span data-stu-id="42211-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="42211-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="42211-170">0x80041006</span></span> | <span data-ttu-id="42211-171">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="42211-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="42211-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="42211-172">0x80041033</span></span> | <span data-ttu-id="42211-173">WMI 是可能已停止和重新啟動。</span><span class="sxs-lookup"><span data-stu-id="42211-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="42211-174">呼叫[ConnectServerWmi](connectserverwmi.md)一次。</span><span class="sxs-lookup"><span data-stu-id="42211-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="42211-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="42211-175">0x80041015</span></span> | <span data-ttu-id="42211-176">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="42211-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="42211-177">0</span><span class="sxs-lookup"><span data-stu-id="42211-177">0</span></span> | <span data-ttu-id="42211-178">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="42211-178">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="42211-179">備註</span><span class="sxs-lookup"><span data-stu-id="42211-179">Remarks</span></span>

<span data-ttu-id="42211-180">此函式會包裝呼叫[IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="42211-180">This function wraps a call to the [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="42211-181">使用者可能無法建立類別以底線 chacater 開頭或結尾的名稱</span><span class="sxs-lookup"><span data-stu-id="42211-181">The user may not create classes with names that begin or end with an underscore chacater</span></span>

<span data-ttu-id="42211-182">如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="42211-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="42211-183">需求</span><span class="sxs-lookup"><span data-stu-id="42211-183">Requirements</span></span>  
 <span data-ttu-id="42211-184">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42211-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42211-185">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="42211-185">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="42211-186">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="42211-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42211-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42211-187">See also</span></span>  
[<span data-ttu-id="42211-188">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="42211-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
