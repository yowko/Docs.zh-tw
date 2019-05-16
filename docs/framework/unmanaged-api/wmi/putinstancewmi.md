---
title: PutInstanceWmi 函式 （Unmanaged API 參考）
description: PutInstanceWmi 函式會建立或更新現有類別的執行個體。
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9774656d010a3e52dd2392094ba6b529a573f3e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636574"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="78c7a-103">PutInstanceWmi 函式</span><span class="sxs-lookup"><span data-stu-id="78c7a-103">PutInstanceWmi function</span></span>

<span data-ttu-id="78c7a-104">建立或更新現有類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="78c7a-105">執行個體是寫入到 WMI 存放庫。</span><span class="sxs-lookup"><span data-stu-id="78c7a-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="78c7a-106">語法</span><span class="sxs-lookup"><span data-stu-id="78c7a-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="78c7a-107">參數</span><span class="sxs-lookup"><span data-stu-id="78c7a-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="78c7a-108">[in]要寫入的執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="78c7a-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="78c7a-109">[in]旗標的組合會影響此函式的行為。</span><span class="sxs-lookup"><span data-stu-id="78c7a-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="78c7a-110">下列的值會定義於*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="78c7a-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="78c7a-111">常數</span><span class="sxs-lookup"><span data-stu-id="78c7a-111">Constant</span></span>  |<span data-ttu-id="78c7a-112">值</span><span class="sxs-lookup"><span data-stu-id="78c7a-112">Value</span></span>  |<span data-ttu-id="78c7a-113">描述</span><span class="sxs-lookup"><span data-stu-id="78c7a-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="78c7a-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="78c7a-114">0x20000</span></span> | <span data-ttu-id="78c7a-115">如果設定，WMI 不會儲存與任何限定詞**Amended**類別。</span><span class="sxs-lookup"><span data-stu-id="78c7a-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="78c7a-116">如果沒有設定，系統會假設此物件不會進行當地語系化，，而且所有的限定詞會儲存與這個執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="78c7a-117">0</span><span class="sxs-lookup"><span data-stu-id="78c7a-117">0</span></span> | <span data-ttu-id="78c7a-118">如果不存在，或是如果它已經存在，覆寫它，請建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="78c7a-119">1</span><span class="sxs-lookup"><span data-stu-id="78c7a-119">1</span></span> | <span data-ttu-id="78c7a-120">更新執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-120">Update the instance.</span></span> <span data-ttu-id="78c7a-121">執行個體必須存在，呼叫才會成功。</span><span class="sxs-lookup"><span data-stu-id="78c7a-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="78c7a-122">2</span><span class="sxs-lookup"><span data-stu-id="78c7a-122">2</span></span> | <span data-ttu-id="78c7a-123">建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-123">Create the instance.</span></span> <span data-ttu-id="78c7a-124">如果執行個體已經存在，則呼叫會失敗。</span><span class="sxs-lookup"><span data-stu-id="78c7a-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="78c7a-125">0x10</span><span class="sxs-lookup"><span data-stu-id="78c7a-125">0x10</span></span> | <span data-ttu-id="78c7a-126">旗標會導致半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="78c7a-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="78c7a-127">[in]一般而言，這個值是`null`。</span><span class="sxs-lookup"><span data-stu-id="78c7a-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="78c7a-128">否則，它是指標[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)可用的提供者所提供的要求的類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="78c7a-129">[out]如果`null`，不使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="78c7a-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="78c7a-130">如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY`，此函式會立即傳回並`WBEM_S_NO_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="78c7a-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="78c7a-131">`ppCallResult`參數會接收到新的指標[IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult)物件。</span><span class="sxs-lookup"><span data-stu-id="78c7a-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="78c7a-132">傳回值</span><span class="sxs-lookup"><span data-stu-id="78c7a-132">Return value</span></span>

<span data-ttu-id="78c7a-133">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="78c7a-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="78c7a-134">常數</span><span class="sxs-lookup"><span data-stu-id="78c7a-134">Constant</span></span>  |<span data-ttu-id="78c7a-135">值</span><span class="sxs-lookup"><span data-stu-id="78c7a-135">Value</span></span>  |<span data-ttu-id="78c7a-136">描述</span><span class="sxs-lookup"><span data-stu-id="78c7a-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="78c7a-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="78c7a-137">0x80041003</span></span> | <span data-ttu-id="78c7a-138">使用者沒有權限來更新指定類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="78c7a-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="78c7a-139">0x80041001</span></span> | <span data-ttu-id="78c7a-140">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="78c7a-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="78c7a-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="78c7a-141">0x80041010</span></span> | <span data-ttu-id="78c7a-142">支援這個執行個體的類別不是有效的。</span><span class="sxs-lookup"><span data-stu-id="78c7a-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="78c7a-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="78c7a-143">0x80041028</span></span> | <span data-ttu-id="78c7a-144">`null`指定的屬性，不能`null`，例如標記**Indexed**或**Not_Null**限定詞。</span><span class="sxs-lookup"><span data-stu-id="78c7a-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="78c7a-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="78c7a-145">0x8004100f</span></span> | <span data-ttu-id="78c7a-146">指定的執行個體不是有效的。</span><span class="sxs-lookup"><span data-stu-id="78c7a-146">The specified instance is not valid.</span></span> <span data-ttu-id="78c7a-147">(例如，呼叫`PutInstanceWmi`類別會傳回此值。)</span><span class="sxs-lookup"><span data-stu-id="78c7a-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="78c7a-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="78c7a-148">0x80041008</span></span> | <span data-ttu-id="78c7a-149">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="78c7a-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="78c7a-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="78c7a-150">0x80041019</span></span> | <span data-ttu-id="78c7a-151">`WBEM_FLAG_CREATE_ONLY`指定旗標，但是執行個體已經存在。</span><span class="sxs-lookup"><span data-stu-id="78c7a-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="78c7a-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="78c7a-152">0x80041002</span></span> | <span data-ttu-id="78c7a-153">`WBEM_FLAG_UPDATE_ONLY` 中指定了`lFlags`，但執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="78c7a-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="78c7a-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="78c7a-154">0x80041006</span></span> | <span data-ttu-id="78c7a-155">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="78c7a-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="78c7a-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="78c7a-156">0x80041033</span></span> | <span data-ttu-id="78c7a-157">WMI 是可能已停止和重新啟動。</span><span class="sxs-lookup"><span data-stu-id="78c7a-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="78c7a-158">呼叫[ConnectServerWmi](connectserverwmi.md)一次。</span><span class="sxs-lookup"><span data-stu-id="78c7a-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="78c7a-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="78c7a-159">0x80041015</span></span> | <span data-ttu-id="78c7a-160">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="78c7a-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="78c7a-161">0</span><span class="sxs-lookup"><span data-stu-id="78c7a-161">0</span></span> | <span data-ttu-id="78c7a-162">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="78c7a-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="78c7a-163">備註</span><span class="sxs-lookup"><span data-stu-id="78c7a-163">Remarks</span></span>

<span data-ttu-id="78c7a-164">此函式會包裝在呼叫[IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance)方法。</span><span class="sxs-lookup"><span data-stu-id="78c7a-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="78c7a-165">`PutInstanceWmi`函數支援建立執行個體和更新現有的類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="78c7a-166">依據`pCtx`參數時，部分或所有執行個體的屬性會更新。</span><span class="sxs-lookup"><span data-stu-id="78c7a-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="78c7a-167">當執行個體所指的`pInst`所屬的子類別化中，而 Windows 管理呼叫的所有提供者負責從子類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="78c7a-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="78c7a-168">所有這些提供者必須能夠順利執行原始`PutInstanceWmi`要求成功。</span><span class="sxs-lookup"><span data-stu-id="78c7a-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="78c7a-169">支援的最上層的類別階層架構中的提供者會先呼叫。</span><span class="sxs-lookup"><span data-stu-id="78c7a-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="78c7a-170">呼叫順序會繼續進行的最上層類別的子類別，以及直到 Windows 管理的提供者擁有所指向的執行個體的類別，從頂端繼續往下`pInst`。</span><span class="sxs-lookup"><span data-stu-id="78c7a-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="78c7a-171">Windows Management 不會呼叫提供者來進行的任何子類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="78c7a-172">當應用程式必須更新所屬的類別階層架構中，執行個體`pInst`參數必須指向包含要修改之屬性的執行個體。</span><span class="sxs-lookup"><span data-stu-id="78c7a-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="78c7a-173">也就是考慮 目標執行個體所屬**ClassB**。</span><span class="sxs-lookup"><span data-stu-id="78c7a-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="78c7a-174">**ClassB**執行個體衍生自**ClassA**，並**ClassA**定義屬性**PropA**。</span><span class="sxs-lookup"><span data-stu-id="78c7a-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="78c7a-175">如果應用程式想要變更的值**PropA**中**ClassB**執行個體，它必須設定`pInst`該執行個體，而不是執行個體**ClassA**.</span><span class="sxs-lookup"><span data-stu-id="78c7a-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="78c7a-176">呼叫`PutInstanceWmi`抽象類別的執行個體上不在允許。</span><span class="sxs-lookup"><span data-stu-id="78c7a-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="78c7a-177">如果函式呼叫失敗，您可以藉由呼叫來取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="78c7a-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="78c7a-178">需求</span><span class="sxs-lookup"><span data-stu-id="78c7a-178">Requirements</span></span>

<span data-ttu-id="78c7a-179">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78c7a-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="78c7a-180">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="78c7a-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="78c7a-181">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="78c7a-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="78c7a-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78c7a-182">See also</span></span>

- [<span data-ttu-id="78c7a-183">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="78c7a-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
