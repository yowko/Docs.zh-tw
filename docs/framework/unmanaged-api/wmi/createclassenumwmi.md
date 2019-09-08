---
title: CreateClassEnumWmi 函式（非受控 API 參考）
description: CreateClassEnumWmi 函數會傳回符合指定準則之所有類別的列舉值。
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a696a6f02f6d3a5afbcb45e5566e4b667739e2c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798737"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="a72d4-103">CreateClassEnumWmi 函式</span><span class="sxs-lookup"><span data-stu-id="a72d4-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="a72d4-104">傳回滿足所指定選取條件之所有類別的列舉程式。</span><span class="sxs-lookup"><span data-stu-id="a72d4-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a72d4-105">語法</span><span class="sxs-lookup"><span data-stu-id="a72d4-105">Syntax</span></span>

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

## <a name="parameters"></a><span data-ttu-id="a72d4-106">參數</span><span class="sxs-lookup"><span data-stu-id="a72d4-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="a72d4-107">在如果不`null`是或空白，會指定父類別的名稱; 枚舉器只會傳回這個類別的子類別。</span><span class="sxs-lookup"><span data-stu-id="a72d4-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="a72d4-108">如果是`null`或空白，而且`lFlags`是 WBEM_FLAG_SHALLOW，則只會傳回最上層類別（沒有父類別的類別）。</span><span class="sxs-lookup"><span data-stu-id="a72d4-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="a72d4-109">如果是`null`或空白，而且`lFlags`為`WBEM_FLAG_DEEP`，則會傳回命名空間中的所有類別。</span><span class="sxs-lookup"><span data-stu-id="a72d4-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="a72d4-110">在會影響此函式行為的旗標組合。</span><span class="sxs-lookup"><span data-stu-id="a72d4-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="a72d4-111">下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="a72d4-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a72d4-112">常數</span><span class="sxs-lookup"><span data-stu-id="a72d4-112">Constant</span></span>  |<span data-ttu-id="a72d4-113">值</span><span class="sxs-lookup"><span data-stu-id="a72d4-113">Value</span></span>  |<span data-ttu-id="a72d4-114">說明</span><span class="sxs-lookup"><span data-stu-id="a72d4-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="a72d4-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="a72d4-115">0x20000</span></span> | <span data-ttu-id="a72d4-116">如果設定，函式會抓取已修改的限定詞，並儲存在目前連接地區設定的當地語系化命名空間中。</span><span class="sxs-lookup"><span data-stu-id="a72d4-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="a72d4-117">如果未設定，此函式只會抓取立即命名空間中儲存的限定詞。</span><span class="sxs-lookup"><span data-stu-id="a72d4-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="a72d4-118">0</span><span class="sxs-lookup"><span data-stu-id="a72d4-118">0</span></span> | <span data-ttu-id="a72d4-119">列舉包括階層中的所有子類別，但不包含這個類別。</span><span class="sxs-lookup"><span data-stu-id="a72d4-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="a72d4-120">1</span><span class="sxs-lookup"><span data-stu-id="a72d4-120">1</span></span> | <span data-ttu-id="a72d4-121">列舉只包含這個類別的純實例，而且會排除提供此類別中找不到之屬性的所有子類別實例。</span><span class="sxs-lookup"><span data-stu-id="a72d4-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="a72d4-122">0x10</span><span class="sxs-lookup"><span data-stu-id="a72d4-122">0x10</span></span> | <span data-ttu-id="a72d4-123">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="a72d4-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="a72d4-124">0x20</span><span class="sxs-lookup"><span data-stu-id="a72d4-124">0x20</span></span> | <span data-ttu-id="a72d4-125">函數會傳回順向列舉值。</span><span class="sxs-lookup"><span data-stu-id="a72d4-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="a72d4-126">一般來說，順向列舉值的速度較快，而且使用的記憶體比傳統的列舉值少，但它們不允許[複製](clone.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a72d4-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="a72d4-127">0</span><span class="sxs-lookup"><span data-stu-id="a72d4-127">0</span></span> | <span data-ttu-id="a72d4-128">WMI 會保留列舉中物件的指標，直到釋放它們為止。</span><span class="sxs-lookup"><span data-stu-id="a72d4-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="a72d4-129">建議的旗標`WBEM_FLAG_RETURN_IMMEDIATELY`為`WBEM_FLAG_FORWARD_ONLY` ，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="a72d4-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="a72d4-130">在通常，此值為`null`。</span><span class="sxs-lookup"><span data-stu-id="a72d4-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="a72d4-131">否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="a72d4-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="a72d4-132">脫銷接收列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="a72d4-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="a72d4-133">在授權層級。</span><span class="sxs-lookup"><span data-stu-id="a72d4-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="a72d4-134">在模擬層級。</span><span class="sxs-lookup"><span data-stu-id="a72d4-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="a72d4-135">在[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件的指標，表示目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a72d4-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="a72d4-136">在使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a72d4-136">[in] The user name.</span></span> <span data-ttu-id="a72d4-137">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="a72d4-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="a72d4-138">在密碼。</span><span class="sxs-lookup"><span data-stu-id="a72d4-138">[in] The password.</span></span> <span data-ttu-id="a72d4-139">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="a72d4-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="a72d4-140">在使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="a72d4-140">[in] The domain name of the user.</span></span> <span data-ttu-id="a72d4-141">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="a72d4-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="a72d4-142">傳回值</span><span class="sxs-lookup"><span data-stu-id="a72d4-142">Return value</span></span>

<span data-ttu-id="a72d4-143">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="a72d4-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a72d4-144">常數</span><span class="sxs-lookup"><span data-stu-id="a72d4-144">Constant</span></span>  |<span data-ttu-id="a72d4-145">值</span><span class="sxs-lookup"><span data-stu-id="a72d4-145">Value</span></span>  |<span data-ttu-id="a72d4-146">描述</span><span class="sxs-lookup"><span data-stu-id="a72d4-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="a72d4-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="a72d4-147">0x80041003</span></span> | <span data-ttu-id="a72d4-148">使用者沒有許可權可查看函數可以傳回的一個或多個類別。</span><span class="sxs-lookup"><span data-stu-id="a72d4-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="a72d4-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a72d4-149">0x80041001</span></span> | <span data-ttu-id="a72d4-150">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a72d4-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="a72d4-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="a72d4-151">0x80041010</span></span> | <span data-ttu-id="a72d4-152">`strSuperClass` 不存在。</span><span class="sxs-lookup"><span data-stu-id="a72d4-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a72d4-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a72d4-153">0x80041008</span></span> | <span data-ttu-id="a72d4-154">參數無效。</span><span class="sxs-lookup"><span data-stu-id="a72d4-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a72d4-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a72d4-155">0x80041006</span></span> | <span data-ttu-id="a72d4-156">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="a72d4-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="a72d4-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="a72d4-157">0x80041033</span></span> | <span data-ttu-id="a72d4-158">WMI 可能已停止並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="a72d4-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="a72d4-159">再次呼叫[ConnectServerWmi](connectserverwmi.md) 。</span><span class="sxs-lookup"><span data-stu-id="a72d4-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="a72d4-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="a72d4-160">0x80041015</span></span> | <span data-ttu-id="a72d4-161">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="a72d4-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a72d4-162">0</span><span class="sxs-lookup"><span data-stu-id="a72d4-162">0</span></span> | <span data-ttu-id="a72d4-163">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a72d4-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a72d4-164">備註</span><span class="sxs-lookup"><span data-stu-id="a72d4-164">Remarks</span></span>

<span data-ttu-id="a72d4-165">此函式會包裝對[IWbemServices：： CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a72d4-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="a72d4-166">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="a72d4-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="a72d4-167">需求</span><span class="sxs-lookup"><span data-stu-id="a72d4-167">Requirements</span></span>

<span data-ttu-id="a72d4-168">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a72d4-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a72d4-169">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a72d4-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a72d4-170">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a72d4-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a72d4-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a72d4-171">See also</span></span>

- [<span data-ttu-id="a72d4-172">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="a72d4-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
