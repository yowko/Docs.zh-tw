---
title: "ConnectServerWmi 函式 （Unmanaged API 參考）"
description: "ConnectServerWmi 函式會使用 DCOM 進行建立的 WMI 命名空間的連接。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b51050bce4603ebcfe99fb38d66e54683c677293
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="0aaa4-103">ConnectServerWmi 函式</span><span class="sxs-lookup"><span data-stu-id="0aaa4-103">ConnectServerWmi function</span></span>
<span data-ttu-id="0aaa4-104">指定在電腦上建立的 WMI 命名空間透過與 DCOM 的連線。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0aaa4-105">語法</span><span class="sxs-lookup"><span data-stu-id="0aaa4-105">Syntax</span></span>  
  
```  
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
## <a name="parameters"></a><span data-ttu-id="0aaa4-106">參數</span><span class="sxs-lookup"><span data-stu-id="0aaa4-106">Parameters</span></span>

<span data-ttu-id="0aaa4-107">`strNetworkResource`[in]有效的指標`BSTR`包含正確的 WMI 命名空間的物件路徑。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="0aaa4-108">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="0aaa4-109">`strUser`[in]有效的指標`BSTR`，其中包含使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="0aaa4-110">A`null`值會指出目前的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="0aaa4-111">如果使用者是目前的不同的網域從`strUser`也可以包含反斜線分隔的網域和使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="0aaa4-112">`strUser`也可以是在使用者主要名稱 (UPN) 格式化，做為 suhc  *userName@domainName* 。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="0aaa4-113">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="0aaa4-114">`strPassword`[in]有效的指標`BSTR`其中包含的密碼。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="0aaa4-115">A`null`指出目前的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="0aaa4-116">空字串 ("") 表示有效長度為零的密碼。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="0aaa4-117">`strLocale`[in]有效的指標`BSTR`，指出資訊擷取正確的地區設定。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="0aaa4-118">Microsoft 地區設定識別項，字串的格式為"MS\_*xxx*"，其中*xxx*是以十六進位格式表示的地區設定識別碼 (LCID) 的字串。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="0aaa4-119">如果未指定無效的地區設定，則方法會傳回`WBEM_E_INVALID_PARAMETER`除了 Windows 7，改為使用伺服器的預設地區設定是。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="0aaa4-120">如果 ' null1，目前的地區設定使用。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="0aaa4-121">`lSecurityFlags`[in]旗標，以傳遞至`ConnectServerWmi`方法。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="0aaa4-122">值為零 (0) 為此參數會導致在呼叫`ConnectServerWmi`建立連接到伺服器之後，才傳回。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="0aaa4-123">這可能導致應用程式沒有回應無限期的伺服器已中斷。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="0aaa4-124">其他有效值為：</span><span class="sxs-lookup"><span data-stu-id="0aaa4-124">The other valid values are:</span></span>

| <span data-ttu-id="0aaa4-125">常數</span><span class="sxs-lookup"><span data-stu-id="0aaa4-125">Constant</span></span>  | <span data-ttu-id="0aaa4-126">值</span><span class="sxs-lookup"><span data-stu-id="0aaa4-126">Value</span></span>  | <span data-ttu-id="0aaa4-127">說明</span><span class="sxs-lookup"><span data-stu-id="0aaa4-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="0aaa4-128">0x40</span><span class="sxs-lookup"><span data-stu-id="0aaa4-128">0x40</span></span> | <span data-ttu-id="0aaa4-129">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-129">Reserved for internal use.</span></span> <span data-ttu-id="0aaa4-130">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="0aaa4-131">0x80</span><span class="sxs-lookup"><span data-stu-id="0aaa4-131">0x80</span></span> | <span data-ttu-id="0aaa4-132">`ConnectServerWmi`傳回在兩分鐘或更短。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="0aaa4-133">`strAuthority`[in]使用者的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="0aaa4-134">它可以包含下列值：</span><span class="sxs-lookup"><span data-stu-id="0aaa4-134">It can have the following values:</span></span>

| <span data-ttu-id="0aaa4-135">值</span><span class="sxs-lookup"><span data-stu-id="0aaa4-135">Value</span></span> | <span data-ttu-id="0aaa4-136">說明</span><span class="sxs-lookup"><span data-stu-id="0aaa4-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="0aaa4-137">空白</span><span class="sxs-lookup"><span data-stu-id="0aaa4-137">blank</span></span> | <span data-ttu-id="0aaa4-138">使用 NTLM 驗證，並會使用目前使用者的 NTLM 網域。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="0aaa4-139">如果`strUser`指定網域 （建議的位置），它必須不在這裡指定。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="0aaa4-140">此函數會傳回`WBEM_E_INVALID_PARAMETER`如果您在這兩個參數中指定的網域。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="0aaa4-141">Kerberos:*主體名稱*</span><span class="sxs-lookup"><span data-stu-id="0aaa4-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="0aaa4-142">使用 Kerberos 驗證，以及這個參數會包含一個 Kerberos 主要名稱。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="0aaa4-143">NTLMDOMAIN:*網域名稱*</span><span class="sxs-lookup"><span data-stu-id="0aaa4-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="0aaa4-144">如果使用 NT LAN Manager 驗證，這個參數會包含 NTLM 網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="0aaa4-145">[in]一般而言，這個參數是`null`。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="0aaa4-146">否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx)所需的一個或多個動態類別提供者的物件。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-146">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="0aaa4-147">[out]此函式傳回時，收到的指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)物件繫結至指定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-147">[out] When the function returns, receives a pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object bound to the specified namespace.</span></span> <span data-ttu-id="0aaa4-148">它設定為指向`null`發生錯誤時。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="0aaa4-149">[in]模擬等級。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="0aaa4-150">[in]授權層級。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="0aaa4-151">傳回值</span><span class="sxs-lookup"><span data-stu-id="0aaa4-151">Return value</span></span>

<span data-ttu-id="0aaa4-152">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="0aaa4-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0aaa4-153">常數</span><span class="sxs-lookup"><span data-stu-id="0aaa4-153">Constant</span></span>  |<span data-ttu-id="0aaa4-154">值</span><span class="sxs-lookup"><span data-stu-id="0aaa4-154">Value</span></span>  |<span data-ttu-id="0aaa4-155">說明</span><span class="sxs-lookup"><span data-stu-id="0aaa4-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="0aaa4-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0aaa4-156">0x80041001</span></span> | <span data-ttu-id="0aaa4-157">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0aaa4-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0aaa4-158">0x80041008</span></span> | <span data-ttu-id="0aaa4-159">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0aaa4-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0aaa4-160">0x80041006</span></span> | <span data-ttu-id="0aaa4-161">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0aaa4-162">0</span><span class="sxs-lookup"><span data-stu-id="0aaa4-162">0</span></span> | <span data-ttu-id="0aaa4-163">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0aaa4-164">備註</span><span class="sxs-lookup"><span data-stu-id="0aaa4-164">Remarks</span></span>

<span data-ttu-id="0aaa4-165">此函式會包裝呼叫[IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="0aaa4-166">在預設命名空間中，本機存取`strNetworkResource`可以是簡單的物件路徑:"b>root\default<b"或"\\.\root\default"。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="0aaa4-167">存取遠端電腦上的預設命名空間使用 COM 或 Microsoft 相容的網路功能，包含電腦名稱:"\\myserver\root\default"。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="0aaa4-168">電腦名稱也可以是 DNS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="0aaa4-169">`ConnectServerWmi`函式也可以執行 IPv6 的電腦連線使用 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="0aaa4-170">`strUser`不可為空字串。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="0aaa4-171">如果網域中指定了`strAuthority`，它必須不也會包含在`strUser`，或函式會傳回`WBEM_E_INVALID_PARAMETER`。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="0aaa4-172">需求</span><span class="sxs-lookup"><span data-stu-id="0aaa4-172">Requirements</span></span>  
 <span data-ttu-id="0aaa4-173">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0aaa4-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aaa4-174">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0aaa4-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0aaa4-175">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0aaa4-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aaa4-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="0aaa4-176">See also</span></span>  
[<span data-ttu-id="0aaa4-177">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="0aaa4-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
