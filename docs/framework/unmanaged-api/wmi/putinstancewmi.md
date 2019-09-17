---
title: PutInstanceWmi 函式（非受控 API 參考）
description: PutInstanceWmi 函數會建立或更新現有類別的實例。
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
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798367"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="9471b-103">PutInstanceWmi 函式</span><span class="sxs-lookup"><span data-stu-id="9471b-103">PutInstanceWmi function</span></span>

<span data-ttu-id="9471b-104">建立或更新現有類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9471b-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="9471b-105">執行個體是寫入到 WMI 存放庫。</span><span class="sxs-lookup"><span data-stu-id="9471b-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9471b-106">語法</span><span class="sxs-lookup"><span data-stu-id="9471b-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="9471b-107">參數</span><span class="sxs-lookup"><span data-stu-id="9471b-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="9471b-108">在要寫入之實例的指標。</span><span class="sxs-lookup"><span data-stu-id="9471b-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="9471b-109">在會影響此函式行為的旗標組合。</span><span class="sxs-lookup"><span data-stu-id="9471b-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="9471b-110">下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="9471b-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9471b-111">常數</span><span class="sxs-lookup"><span data-stu-id="9471b-111">Constant</span></span>  |<span data-ttu-id="9471b-112">值</span><span class="sxs-lookup"><span data-stu-id="9471b-112">Value</span></span>  |<span data-ttu-id="9471b-113">描述</span><span class="sxs-lookup"><span data-stu-id="9471b-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="9471b-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="9471b-114">0x20000</span></span> | <span data-ttu-id="9471b-115">如果設定，WMI 不會將任何限定詞儲存為**修改**過的類別。</span><span class="sxs-lookup"><span data-stu-id="9471b-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="9471b-116">如果未設定，則會假設此物件未當地語系化，而且所有限定詞都會與這個實例一起儲存。</span><span class="sxs-lookup"><span data-stu-id="9471b-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="9471b-117">0</span><span class="sxs-lookup"><span data-stu-id="9471b-117">0</span></span> | <span data-ttu-id="9471b-118">如果實例不存在，請建立它，如果它已經存在，則予以覆寫。</span><span class="sxs-lookup"><span data-stu-id="9471b-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="9471b-119">1</span><span class="sxs-lookup"><span data-stu-id="9471b-119">1</span></span> | <span data-ttu-id="9471b-120">更新實例。</span><span class="sxs-lookup"><span data-stu-id="9471b-120">Update the instance.</span></span> <span data-ttu-id="9471b-121">實例必須存在，呼叫才會成功。</span><span class="sxs-lookup"><span data-stu-id="9471b-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="9471b-122">2</span><span class="sxs-lookup"><span data-stu-id="9471b-122">2</span></span> | <span data-ttu-id="9471b-123">建立實例。</span><span class="sxs-lookup"><span data-stu-id="9471b-123">Create the instance.</span></span> <span data-ttu-id="9471b-124">如果實例已經存在，呼叫就會失敗。</span><span class="sxs-lookup"><span data-stu-id="9471b-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="9471b-125">0x10</span><span class="sxs-lookup"><span data-stu-id="9471b-125">0x10</span></span> | <span data-ttu-id="9471b-126">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="9471b-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="9471b-127">在通常，此值為`null`。</span><span class="sxs-lookup"><span data-stu-id="9471b-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="9471b-128">否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="9471b-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="9471b-129">脫銷如果`null`為，則不會使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="9471b-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="9471b-130">如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY` ，`WBEM_S_NO_ERROR`則函式會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="9471b-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="9471b-131">`ppCallResult` 參數會接收新 [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="9471b-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="9471b-132">傳回值</span><span class="sxs-lookup"><span data-stu-id="9471b-132">Return value</span></span>

<span data-ttu-id="9471b-133">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="9471b-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9471b-134">常數</span><span class="sxs-lookup"><span data-stu-id="9471b-134">Constant</span></span>  |<span data-ttu-id="9471b-135">值</span><span class="sxs-lookup"><span data-stu-id="9471b-135">Value</span></span>  |<span data-ttu-id="9471b-136">描述</span><span class="sxs-lookup"><span data-stu-id="9471b-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="9471b-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="9471b-137">0x80041003</span></span> | <span data-ttu-id="9471b-138">使用者沒有許可權可更新指定之類別的實例。</span><span class="sxs-lookup"><span data-stu-id="9471b-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="9471b-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9471b-139">0x80041001</span></span> | <span data-ttu-id="9471b-140">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9471b-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="9471b-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="9471b-141">0x80041010</span></span> | <span data-ttu-id="9471b-142">支援這個實例的類別無效。</span><span class="sxs-lookup"><span data-stu-id="9471b-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="9471b-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="9471b-143">0x80041028</span></span> | <span data-ttu-id="9471b-144">針對不能為`null`的屬性指定，例如由**索引**或 Not_Null 限定詞標記的。 `null`</span><span class="sxs-lookup"><span data-stu-id="9471b-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="9471b-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="9471b-145">0x8004100f</span></span> | <span data-ttu-id="9471b-146">指定的實例無效。</span><span class="sxs-lookup"><span data-stu-id="9471b-146">The specified instance is not valid.</span></span> <span data-ttu-id="9471b-147">（例如，使用類別`PutInstanceWmi`呼叫會傳回這個值）。</span><span class="sxs-lookup"><span data-stu-id="9471b-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9471b-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9471b-148">0x80041008</span></span> | <span data-ttu-id="9471b-149">參數無效。</span><span class="sxs-lookup"><span data-stu-id="9471b-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="9471b-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="9471b-150">0x80041019</span></span> | <span data-ttu-id="9471b-151">已`WBEM_FLAG_CREATE_ONLY`指定旗標，但實例已經存在。</span><span class="sxs-lookup"><span data-stu-id="9471b-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="9471b-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9471b-152">0x80041002</span></span> | <span data-ttu-id="9471b-153">`WBEM_FLAG_UPDATE_ONLY`已在中`lFlags`指定，但實例不存在。</span><span class="sxs-lookup"><span data-stu-id="9471b-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9471b-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9471b-154">0x80041006</span></span> | <span data-ttu-id="9471b-155">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="9471b-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="9471b-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="9471b-156">0x80041033</span></span> | <span data-ttu-id="9471b-157">WMI 可能已停止並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="9471b-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="9471b-158">再次呼叫[ConnectServerWmi](connectserverwmi.md) 。</span><span class="sxs-lookup"><span data-stu-id="9471b-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="9471b-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="9471b-159">0x80041015</span></span> | <span data-ttu-id="9471b-160">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="9471b-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9471b-161">0</span><span class="sxs-lookup"><span data-stu-id="9471b-161">0</span></span> | <span data-ttu-id="9471b-162">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="9471b-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9471b-163">備註</span><span class="sxs-lookup"><span data-stu-id="9471b-163">Remarks</span></span>

<span data-ttu-id="9471b-164">此函式會包裝對[IWbemServices：:P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9471b-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="9471b-165">`PutInstanceWmi`函數只支援建立實例，以及更新現有類別的實例。</span><span class="sxs-lookup"><span data-stu-id="9471b-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="9471b-166">視`pCtx`參數的設定方式而定，會更新實例的部分或所有屬性。</span><span class="sxs-lookup"><span data-stu-id="9471b-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="9471b-167">當所指`pInst`的實例屬於子類別時，Windows 管理會呼叫所有負責子類別衍生來源的提供者。</span><span class="sxs-lookup"><span data-stu-id="9471b-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="9471b-168">所有這些提供者都必須成功，原始`PutInstanceWmi`要求才會成功。</span><span class="sxs-lookup"><span data-stu-id="9471b-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="9471b-169">首先會呼叫支援階層中最上層類別的提供者。</span><span class="sxs-lookup"><span data-stu-id="9471b-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="9471b-170">呼叫順序會繼續使用最上層類別的子類別，並從上到下繼續進行，直到 Windows 管理到達擁有所指向`pInst`之實例的類別提供者為止。</span><span class="sxs-lookup"><span data-stu-id="9471b-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="9471b-171">Windows 管理不會呼叫實例之任何子類別的提供者。</span><span class="sxs-lookup"><span data-stu-id="9471b-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="9471b-172">當應用程式必須更新屬於類別階層的實例時， `pInst`參數必須指向包含要修改之屬性的實例。</span><span class="sxs-lookup"><span data-stu-id="9471b-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="9471b-173">也就是，請考慮屬於**ClassB**的目標實例。</span><span class="sxs-lookup"><span data-stu-id="9471b-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="9471b-174">**ClassB**實例衍生自**ClassA**，而**ClassA**定義屬性**PropA**。</span><span class="sxs-lookup"><span data-stu-id="9471b-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="9471b-175">如果應用程式想要變更**ClassB**實例中的`pInst` **PropA**值，它必須將設定為該實例，而不是**ClassA**的實例。</span><span class="sxs-lookup"><span data-stu-id="9471b-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="9471b-176">不`PutInstanceWmi`允許在抽象類別的實例上呼叫。</span><span class="sxs-lookup"><span data-stu-id="9471b-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="9471b-177">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="9471b-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9471b-178">需求</span><span class="sxs-lookup"><span data-stu-id="9471b-178">Requirements</span></span>

<span data-ttu-id="9471b-179">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9471b-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9471b-180">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9471b-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="9471b-181">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9471b-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9471b-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9471b-182">See also</span></span>

- [<span data-ttu-id="9471b-183">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="9471b-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
