---
title: CreateInstanceEnumWmi 函式（非受控 API 參考）
description: CreateInstanceEnumWmi 函數會傳回枚舉器，其中包含符合選取準則的指定類別實例。
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7709d9c50a494013ece2f91b3acc213278f0e57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798900"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="021a1-103">CreateInstanceEnumWmi 函式</span><span class="sxs-lookup"><span data-stu-id="021a1-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="021a1-104">傳回會傳回滿足指定選取條件之指定類別執行個體的列舉程式。</span><span class="sxs-lookup"><span data-stu-id="021a1-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="021a1-105">語法</span><span class="sxs-lookup"><span data-stu-id="021a1-105">Syntax</span></span>

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="021a1-106">參數</span><span class="sxs-lookup"><span data-stu-id="021a1-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="021a1-107">在需要實例的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="021a1-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="021a1-108">這個參數不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="021a1-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="021a1-109">在會影響此函式行為的旗標組合。</span><span class="sxs-lookup"><span data-stu-id="021a1-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="021a1-110">下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="021a1-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="021a1-111">常數</span><span class="sxs-lookup"><span data-stu-id="021a1-111">Constant</span></span>  |<span data-ttu-id="021a1-112">值</span><span class="sxs-lookup"><span data-stu-id="021a1-112">Value</span></span>  |<span data-ttu-id="021a1-113">描述</span><span class="sxs-lookup"><span data-stu-id="021a1-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="021a1-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="021a1-114">0x20000</span></span> | <span data-ttu-id="021a1-115">如果設定，函式會抓取已修改的限定詞，並儲存在目前連接地區設定的當地語系化命名空間中。</span><span class="sxs-lookup"><span data-stu-id="021a1-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="021a1-116">如果未設定，此函式只會抓取立即命名空間中儲存的限定詞。</span><span class="sxs-lookup"><span data-stu-id="021a1-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="021a1-117">0</span><span class="sxs-lookup"><span data-stu-id="021a1-117">0</span></span> | <span data-ttu-id="021a1-118">列舉包含此階層中的這個和所有子類別。</span><span class="sxs-lookup"><span data-stu-id="021a1-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="021a1-119">1</span><span class="sxs-lookup"><span data-stu-id="021a1-119">1</span></span> | <span data-ttu-id="021a1-120">列舉只包含這個類別的純實例，而且會排除提供此類別中找不到之屬性的所有子類別實例。</span><span class="sxs-lookup"><span data-stu-id="021a1-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="021a1-121">0x10</span><span class="sxs-lookup"><span data-stu-id="021a1-121">0x10</span></span> | <span data-ttu-id="021a1-122">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="021a1-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="021a1-123">0x20</span><span class="sxs-lookup"><span data-stu-id="021a1-123">0x20</span></span> | <span data-ttu-id="021a1-124">函數會傳回順向列舉值。</span><span class="sxs-lookup"><span data-stu-id="021a1-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="021a1-125">一般來說，順向列舉值的速度較快，而且使用的記憶體比傳統的列舉值少，但它們不允許[複製](clone.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="021a1-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="021a1-126">0</span><span class="sxs-lookup"><span data-stu-id="021a1-126">0</span></span> | <span data-ttu-id="021a1-127">WMI 會保留列舉中物件的指標，直到釋放它們為止。</span><span class="sxs-lookup"><span data-stu-id="021a1-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="021a1-128">建議的旗標`WBEM_FLAG_RETURN_IMMEDIATELY`為`WBEM_FLAG_FORWARD_ONLY` ，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="021a1-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="021a1-129">在通常，此值為`null`。</span><span class="sxs-lookup"><span data-stu-id="021a1-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="021a1-130">否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供要求之實例的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="021a1-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="021a1-131">脫銷接收列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="021a1-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="021a1-132">在授權層級。</span><span class="sxs-lookup"><span data-stu-id="021a1-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="021a1-133">在模擬層級。</span><span class="sxs-lookup"><span data-stu-id="021a1-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="021a1-134">在[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件的指標，表示目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="021a1-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="021a1-135">在使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="021a1-135">[in] The user name.</span></span> <span data-ttu-id="021a1-136">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="021a1-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="021a1-137">在密碼。</span><span class="sxs-lookup"><span data-stu-id="021a1-137">[in] The password.</span></span> <span data-ttu-id="021a1-138">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="021a1-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="021a1-139">在使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="021a1-139">[in] The domain name of the user.</span></span> <span data-ttu-id="021a1-140">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="021a1-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="021a1-141">傳回值</span><span class="sxs-lookup"><span data-stu-id="021a1-141">Return value</span></span>

<span data-ttu-id="021a1-142">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="021a1-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="021a1-143">常數</span><span class="sxs-lookup"><span data-stu-id="021a1-143">Constant</span></span>  |<span data-ttu-id="021a1-144">值</span><span class="sxs-lookup"><span data-stu-id="021a1-144">Value</span></span>  |<span data-ttu-id="021a1-145">說明</span><span class="sxs-lookup"><span data-stu-id="021a1-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="021a1-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="021a1-146">0x80041003</span></span> | <span data-ttu-id="021a1-147">使用者沒有許可權可查看指定之類別的實例。</span><span class="sxs-lookup"><span data-stu-id="021a1-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="021a1-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="021a1-148">0x80041001</span></span> | <span data-ttu-id="021a1-149">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="021a1-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="021a1-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="021a1-150">0x80041010</span></span> | <span data-ttu-id="021a1-151">`strFilter` 不存在。</span><span class="sxs-lookup"><span data-stu-id="021a1-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="021a1-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="021a1-152">0x80041008</span></span> | <span data-ttu-id="021a1-153">參數無效。</span><span class="sxs-lookup"><span data-stu-id="021a1-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="021a1-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="021a1-154">0x80041006</span></span> | <span data-ttu-id="021a1-155">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="021a1-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="021a1-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="021a1-156">0x80041033</span></span> | <span data-ttu-id="021a1-157">WMI 可能已停止並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="021a1-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="021a1-158">再次呼叫[ConnectServerWmi](connectserverwmi.md) 。</span><span class="sxs-lookup"><span data-stu-id="021a1-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="021a1-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="021a1-159">0x80041015</span></span> | <span data-ttu-id="021a1-160">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="021a1-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="021a1-161">0</span><span class="sxs-lookup"><span data-stu-id="021a1-161">0</span></span> | <span data-ttu-id="021a1-162">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="021a1-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="021a1-163">備註</span><span class="sxs-lookup"><span data-stu-id="021a1-163">Remarks</span></span>

<span data-ttu-id="021a1-164">此函式會包裝對[IWbemServices：： CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="021a1-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="021a1-165">請注意，傳回的列舉值可以有零個元素。</span><span class="sxs-lookup"><span data-stu-id="021a1-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="021a1-166">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="021a1-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="021a1-167">需求</span><span class="sxs-lookup"><span data-stu-id="021a1-167">Requirements</span></span>

<span data-ttu-id="021a1-168">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="021a1-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="021a1-169">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="021a1-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="021a1-170">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="021a1-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="021a1-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="021a1-171">See also</span></span>

- [<span data-ttu-id="021a1-172">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="021a1-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
