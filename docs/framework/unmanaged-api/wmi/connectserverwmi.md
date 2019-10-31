---
title: ConnectServerWmi 函式（非受控 API 參考）
description: ConnectServerWmi 函數會使用 DCOM 來建立與 WMI 命名空間的連線。
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 25a73060ed242fd0e77042cd0ea9618b9b27250f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128684"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="20f87-103">ConnectServerWmi 函式</span><span class="sxs-lookup"><span data-stu-id="20f87-103">ConnectServerWmi function</span></span>

<span data-ttu-id="20f87-104">在指定的電腦上建立從 DCOM 到 WMI 命名空間的連線。</span><span class="sxs-lookup"><span data-stu-id="20f87-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="20f87-105">語法</span><span class="sxs-lookup"><span data-stu-id="20f87-105">Syntax</span></span>

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a><span data-ttu-id="20f87-106">參數</span><span class="sxs-lookup"><span data-stu-id="20f87-106">Parameters</span></span>

`strNetworkResource`\
<span data-ttu-id="20f87-107">在有效 `BSTR` 的指標，其中包含正確 WMI 命名空間的物件路徑。</span><span class="sxs-lookup"><span data-stu-id="20f87-107">[in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="20f87-108">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="20f87-108">See the [Remarks](#remarks) section for more information.</span></span>

`strUser`\
<span data-ttu-id="20f87-109">在包含使用者名稱之有效 `BSTR` 的指標。</span><span class="sxs-lookup"><span data-stu-id="20f87-109">[in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="20f87-110">`null` 值，表示目前的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="20f87-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="20f87-111">如果使用者與目前的網域不同，則 `strUser` 也可以包含以反斜線分隔的網域和使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="20f87-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="20f87-112">`strUser` 也可以是使用者主體名稱（UPN）格式，例如 `userName@domainName`。</span><span class="sxs-lookup"><span data-stu-id="20f87-112">`strUser` can also be in user principal name (UPN) format, such as `userName@domainName`.</span></span> <span data-ttu-id="20f87-113">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="20f87-113">See the [Remarks](#remarks) section for more information.</span></span>

`strPassword`\
<span data-ttu-id="20f87-114">在包含密碼之有效 `BSTR` 的指標。</span><span class="sxs-lookup"><span data-stu-id="20f87-114">[in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="20f87-115">`null` 表示目前的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="20f87-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="20f87-116">空字串（""）表示有效的長度為零的密碼。</span><span class="sxs-lookup"><span data-stu-id="20f87-116">An empty string ("") indicates a valid zero-length password.</span></span>

`strLocale`\
<span data-ttu-id="20f87-117">在有效 `BSTR` 的指標，表示資訊抓取的正確地區設定。</span><span class="sxs-lookup"><span data-stu-id="20f87-117">[in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="20f87-118">針對 Microsoft 地區設定識別碼，字串的格式為 "MS\_*xxx*"，其中*xxx*是十六進位格式的字串，表示地區設定識別碼（LCID）。</span><span class="sxs-lookup"><span data-stu-id="20f87-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="20f87-119">如果指定了不正確地區設定，此方法會傳回 `WBEM_E_INVALID_PARAMETER`，但是在 Windows 7 上，會改為使用伺服器的預設地區設定。</span><span class="sxs-lookup"><span data-stu-id="20f87-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="20f87-120">如果為 ' null1，則會使用目前的地區設定。</span><span class="sxs-lookup"><span data-stu-id="20f87-120">If \`null1, the current locale is used.</span></span>

`lSecurityFlags`\
<span data-ttu-id="20f87-121">在要傳遞至 `ConnectServerWmi` 方法的旗標。</span><span class="sxs-lookup"><span data-stu-id="20f87-121">[in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="20f87-122">這個參數的值為零（0），會導致只有在建立與伺服器的連接之後，才會呼叫 `ConnectServerWmi`。</span><span class="sxs-lookup"><span data-stu-id="20f87-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="20f87-123">這可能會導致應用程式在伺服器中斷時不會無限期回應。</span><span class="sxs-lookup"><span data-stu-id="20f87-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="20f87-124">其他有效的值為：</span><span class="sxs-lookup"><span data-stu-id="20f87-124">The other valid values are:</span></span>

| <span data-ttu-id="20f87-125">常數</span><span class="sxs-lookup"><span data-stu-id="20f87-125">Constant</span></span>  | <span data-ttu-id="20f87-126">值</span><span class="sxs-lookup"><span data-stu-id="20f87-126">Value</span></span>  | <span data-ttu-id="20f87-127">描述</span><span class="sxs-lookup"><span data-stu-id="20f87-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="20f87-128">0x40</span><span class="sxs-lookup"><span data-stu-id="20f87-128">0x40</span></span> | <span data-ttu-id="20f87-129">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="20f87-129">Reserved for internal use.</span></span> <span data-ttu-id="20f87-130">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="20f87-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="20f87-131">0x80</span><span class="sxs-lookup"><span data-stu-id="20f87-131">0x80</span></span> | <span data-ttu-id="20f87-132">`ConnectServerWmi` 會在兩分鐘內傳回。</span><span class="sxs-lookup"><span data-stu-id="20f87-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

`strAuthority`\
<span data-ttu-id="20f87-133">在使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="20f87-133">[in] The domain name of the user.</span></span> <span data-ttu-id="20f87-134">它可以包含下列值：</span><span class="sxs-lookup"><span data-stu-id="20f87-134">It can have the following values:</span></span>

| <span data-ttu-id="20f87-135">值</span><span class="sxs-lookup"><span data-stu-id="20f87-135">Value</span></span> | <span data-ttu-id="20f87-136">描述</span><span class="sxs-lookup"><span data-stu-id="20f87-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="20f87-137">空白</span><span class="sxs-lookup"><span data-stu-id="20f87-137">blank</span></span> | <span data-ttu-id="20f87-138">使用 NTLM 驗證，並使用目前使用者的 NTLM 網域。</span><span class="sxs-lookup"><span data-stu-id="20f87-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="20f87-139">如果 `strUser` 指定網域（建議的位置），則不得在此指定。</span><span class="sxs-lookup"><span data-stu-id="20f87-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="20f87-140">如果您在這兩個參數中指定網域，此函數會傳回 `WBEM_E_INVALID_PARAMETER`。</span><span class="sxs-lookup"><span data-stu-id="20f87-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="20f87-141">Kerberos：*主體名稱*</span><span class="sxs-lookup"><span data-stu-id="20f87-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="20f87-142">使用 kerberos 驗證，且此參數包含 Kerberos 主體名稱。</span><span class="sxs-lookup"><span data-stu-id="20f87-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="20f87-143">NTLMDOMAIN：*功能變數名稱*</span><span class="sxs-lookup"><span data-stu-id="20f87-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="20f87-144">使用 NT LAN Manager 驗證，且此參數包含 NTLM 功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="20f87-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`\
<span data-ttu-id="20f87-145">在一般而言，此參數是 `null`。</span><span class="sxs-lookup"><span data-stu-id="20f87-145">[in] Typically, this parameter is `null`.</span></span> <span data-ttu-id="20f87-146">否則，它是一或多個動態類別提供者所需之[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="20f87-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span>

`ppNamespace`\
<span data-ttu-id="20f87-147">脫銷當函式傳回時，會接收系結至指定之命名空間之[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="20f87-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="20f87-148">當發生錯誤時，它會設定為指向 `null`。</span><span class="sxs-lookup"><span data-stu-id="20f87-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`\
<span data-ttu-id="20f87-149">在模擬層級。</span><span class="sxs-lookup"><span data-stu-id="20f87-149">[in] The impersonation level.</span></span>

`authLevel`\
<span data-ttu-id="20f87-150">在授權層級。</span><span class="sxs-lookup"><span data-stu-id="20f87-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="20f87-151">傳回值</span><span class="sxs-lookup"><span data-stu-id="20f87-151">Return value</span></span>

<span data-ttu-id="20f87-152">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="20f87-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="20f87-153">常數</span><span class="sxs-lookup"><span data-stu-id="20f87-153">Constant</span></span>  |<span data-ttu-id="20f87-154">值</span><span class="sxs-lookup"><span data-stu-id="20f87-154">Value</span></span>  |<span data-ttu-id="20f87-155">描述</span><span class="sxs-lookup"><span data-stu-id="20f87-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="20f87-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="20f87-156">0x80041001</span></span> | <span data-ttu-id="20f87-157">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="20f87-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="20f87-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="20f87-158">0x80041008</span></span> | <span data-ttu-id="20f87-159">參數無效。</span><span class="sxs-lookup"><span data-stu-id="20f87-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="20f87-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="20f87-160">0x80041006</span></span> | <span data-ttu-id="20f87-161">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="20f87-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="20f87-162">0</span><span class="sxs-lookup"><span data-stu-id="20f87-162">0</span></span> | <span data-ttu-id="20f87-163">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="20f87-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="20f87-164">備註</span><span class="sxs-lookup"><span data-stu-id="20f87-164">Remarks</span></span>

<span data-ttu-id="20f87-165">此函式會包裝對[IWbemLocator：： ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="20f87-165">This function wraps a call to the [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) method.</span></span>

<span data-ttu-id="20f87-166">對於預設命名空間的本機存取，`strNetworkResource` 可以是簡單的物件路徑： "root\default" 或 "\\.\root\default"。</span><span class="sxs-lookup"><span data-stu-id="20f87-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="20f87-167">若要使用 COM 或與 Microsoft 相容的網路存取遠端電腦上的預設命名空間，請包括電腦名稱稱： "\\myserver\root\default"。</span><span class="sxs-lookup"><span data-stu-id="20f87-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="20f87-168">電腦名稱稱也可以是 DNS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="20f87-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="20f87-169">`ConnectServerWmi` 函式也可以使用 IPv6 位址，與執行 IPv6 的電腦進行連接。</span><span class="sxs-lookup"><span data-stu-id="20f87-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="20f87-170">`strUser` 不可以是空字串。</span><span class="sxs-lookup"><span data-stu-id="20f87-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="20f87-171">如果在 `strAuthority`中指定了網域，它也不能包含在 `strUser`中，或函數會傳回 `WBEM_E_INVALID_PARAMETER`。</span><span class="sxs-lookup"><span data-stu-id="20f87-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>

## <a name="requirements"></a><span data-ttu-id="20f87-172">需求</span><span class="sxs-lookup"><span data-stu-id="20f87-172">Requirements</span></span>

 <span data-ttu-id="20f87-173">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20f87-173">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="20f87-174">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="20f87-174">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="20f87-175">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="20f87-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="20f87-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="20f87-176">See also</span></span>

- [<span data-ttu-id="20f87-177">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="20f87-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
