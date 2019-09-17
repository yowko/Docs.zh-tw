---
title: PutClassWmi 函式（非受控 API 參考）
description: PutClassWmi 函數會建立新的類別，或更新現有的類別。
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fcf879705135e0093868b48580a37f9d46aa594
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798388"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="32097-103">PutClassWmi 函式</span><span class="sxs-lookup"><span data-stu-id="32097-103">PutClassWmi function</span></span>

<span data-ttu-id="32097-104">建立新類別或更新現有類別。</span><span class="sxs-lookup"><span data-stu-id="32097-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="32097-105">語法</span><span class="sxs-lookup"><span data-stu-id="32097-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="32097-106">參數</span><span class="sxs-lookup"><span data-stu-id="32097-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="32097-107">在有效類別定義的指標。</span><span class="sxs-lookup"><span data-stu-id="32097-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="32097-108">必須使用所有必要的屬性值正確地初始化。</span><span class="sxs-lookup"><span data-stu-id="32097-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="32097-109">在會影響此函式行為的旗標組合。</span><span class="sxs-lookup"><span data-stu-id="32097-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="32097-110">下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="32097-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="32097-111">常數</span><span class="sxs-lookup"><span data-stu-id="32097-111">Constant</span></span>  |<span data-ttu-id="32097-112">值</span><span class="sxs-lookup"><span data-stu-id="32097-112">Value</span></span>  |<span data-ttu-id="32097-113">說明</span><span class="sxs-lookup"><span data-stu-id="32097-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="32097-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="32097-114">0x20000</span></span> | <span data-ttu-id="32097-115">如果設定，WMI 不會將任何限定詞儲存為修改過的類別。</span><span class="sxs-lookup"><span data-stu-id="32097-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="32097-116">如果未設定，則會假設此物件未當地語系化，而且所有限定詞都會與這個實例一起儲存。</span><span class="sxs-lookup"><span data-stu-id="32097-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="32097-117">0</span><span class="sxs-lookup"><span data-stu-id="32097-117">0</span></span> | <span data-ttu-id="32097-118">如果類別不存在，請建立它，如果已存在，則予以覆寫。</span><span class="sxs-lookup"><span data-stu-id="32097-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="32097-119">1</span><span class="sxs-lookup"><span data-stu-id="32097-119">1</span></span> | <span data-ttu-id="32097-120">更新類別。</span><span class="sxs-lookup"><span data-stu-id="32097-120">Update the class.</span></span> <span data-ttu-id="32097-121">類別必須存在，呼叫才會成功。</span><span class="sxs-lookup"><span data-stu-id="32097-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="32097-122">2</span><span class="sxs-lookup"><span data-stu-id="32097-122">2</span></span> | <span data-ttu-id="32097-123">建立類別。</span><span class="sxs-lookup"><span data-stu-id="32097-123">Create the class.</span></span> <span data-ttu-id="32097-124">如果類別已經存在，呼叫就會失敗。</span><span class="sxs-lookup"><span data-stu-id="32097-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="32097-125">0x10</span><span class="sxs-lookup"><span data-stu-id="32097-125">0x10</span></span> | <span data-ttu-id="32097-126">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="32097-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="32097-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="32097-127">0x10000</span></span> | <span data-ttu-id="32097-128">呼叫`PutClassWmi`時，推播提供者必須指定此旗標，以指出這個類別已變更。</span><span class="sxs-lookup"><span data-stu-id="32097-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="32097-129">0</span><span class="sxs-lookup"><span data-stu-id="32097-129">0</span></span> | <span data-ttu-id="32097-130">如果沒有衍生類別，而且沒有該類別的實例，則允許更新類別。</span><span class="sxs-lookup"><span data-stu-id="32097-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="32097-131">如果變更僅限於不重要的限定詞（例如描述辨識符號），它也可讓您在所有情況下進行更新。</span><span class="sxs-lookup"><span data-stu-id="32097-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="32097-132">如果類別有實例或變更為重要的限定詞，則更新會失敗。</span><span class="sxs-lookup"><span data-stu-id="32097-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="32097-133">0x20</span><span class="sxs-lookup"><span data-stu-id="32097-133">0x20</span></span> | <span data-ttu-id="32097-134">即使有子類別，也允許更新類別，但前提是變更不會造成與子類別的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="32097-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="32097-135">例如，此旗標可讓新的屬性新增至先前未在任何子類別中提及的基類。</span><span class="sxs-lookup"><span data-stu-id="32097-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="32097-136">如果類別有實例，則更新會失敗。</span><span class="sxs-lookup"><span data-stu-id="32097-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="32097-137">0x40</span><span class="sxs-lookup"><span data-stu-id="32097-137">0x40</span></span> | <span data-ttu-id="32097-138">當存在衝突的子類別時，強制更新類別。</span><span class="sxs-lookup"><span data-stu-id="32097-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="32097-139">例如，如果在子類別中定義了類別限定詞，而且基類嘗試加入與現有的限定詞衝突，則此旗標會強制更新。</span><span class="sxs-lookup"><span data-stu-id="32097-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="32097-140">在強制模式中，會藉由刪除子類別中衝突的限定詞來解決 tis 衝突。</span><span class="sxs-lookup"><span data-stu-id="32097-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="32097-141">在通常，此值為`null`。</span><span class="sxs-lookup"><span data-stu-id="32097-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="32097-142">否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="32097-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="32097-143">脫銷如果`null`為，則不會使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="32097-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="32097-144">如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY` ，`WBEM_S_NO_ERROR`則函式會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="32097-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="32097-145">`ppCallResult` 參數會接收新 [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="32097-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="32097-146">傳回值</span><span class="sxs-lookup"><span data-stu-id="32097-146">Return value</span></span>

<span data-ttu-id="32097-147">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="32097-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="32097-148">常數</span><span class="sxs-lookup"><span data-stu-id="32097-148">Constant</span></span>  |<span data-ttu-id="32097-149">值</span><span class="sxs-lookup"><span data-stu-id="32097-149">Value</span></span>  |<span data-ttu-id="32097-150">描述</span><span class="sxs-lookup"><span data-stu-id="32097-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="32097-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="32097-151">0x80041003</span></span> | <span data-ttu-id="32097-152">使用者沒有建立或修改類別的許可權。</span><span class="sxs-lookup"><span data-stu-id="32097-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="32097-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="32097-153">0x80041001</span></span> | <span data-ttu-id="32097-154">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="32097-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="32097-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="32097-155">0x80041010</span></span> | <span data-ttu-id="32097-156">指定的類別無效。</span><span class="sxs-lookup"><span data-stu-id="32097-156">The specified class is not valid.</span></span> <span data-ttu-id="32097-157">一般而言，這表示會`pObject`指定實例物件。</span><span class="sxs-lookup"><span data-stu-id="32097-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="32097-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="32097-158">0x80041008</span></span> | <span data-ttu-id="32097-159">參數無效。</span><span class="sxs-lookup"><span data-stu-id="32097-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="32097-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="32097-160">0x80041016</span></span> | <span data-ttu-id="32097-161">指定的類別名稱無效。</span><span class="sxs-lookup"><span data-stu-id="32097-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="32097-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="32097-162">0x80041025</span></span> | <span data-ttu-id="32097-163">嘗試進行會使子類別失效的變更。</span><span class="sxs-lookup"><span data-stu-id="32097-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="32097-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="32097-164">0x80041019</span></span> | <span data-ttu-id="32097-165">已`WBEM_FLAG_CREATE_ONLY`指定旗標，但類別已經存在。</span><span class="sxs-lookup"><span data-stu-id="32097-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="32097-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="32097-166">0x80041002</span></span> | <span data-ttu-id="32097-167">`WBEM_FLAG_UPDATE_ONLY`在中`lFlags`指定了，而且找不到類別。</span><span class="sxs-lookup"><span data-stu-id="32097-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="32097-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="32097-168">0x80041020</span></span> | <span data-ttu-id="32097-169">尚未設定類別的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="32097-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="32097-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="32097-170">0x80041006</span></span> | <span data-ttu-id="32097-171">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="32097-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="32097-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="32097-172">0x80041033</span></span> | <span data-ttu-id="32097-173">WMI 可能已停止並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="32097-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="32097-174">再次呼叫[ConnectServerWmi](connectserverwmi.md) 。</span><span class="sxs-lookup"><span data-stu-id="32097-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="32097-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="32097-175">0x80041015</span></span> | <span data-ttu-id="32097-176">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="32097-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="32097-177">0</span><span class="sxs-lookup"><span data-stu-id="32097-177">0</span></span> | <span data-ttu-id="32097-178">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="32097-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="32097-179">備註</span><span class="sxs-lookup"><span data-stu-id="32097-179">Remarks</span></span>

<span data-ttu-id="32097-180">此函式會包裝對[IWbemServices：:P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="32097-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="32097-181">使用者不得以底線字元來建立名稱開頭或結尾的類別。</span><span class="sxs-lookup"><span data-stu-id="32097-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="32097-182">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="32097-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="32097-183">需求</span><span class="sxs-lookup"><span data-stu-id="32097-183">Requirements</span></span>

<span data-ttu-id="32097-184">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32097-184">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="32097-185">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="32097-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="32097-186">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32097-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="32097-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32097-187">See also</span></span>

- [<span data-ttu-id="32097-188">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="32097-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
