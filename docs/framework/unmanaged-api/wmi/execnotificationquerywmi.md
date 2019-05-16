---
title: ExecNotificationQueryWmi 函式 （Unmanaged API 參考）
description: ExecNotificationQueryWmi 函式會執行查詢，以接收事件。
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa2233bab82f3cd4d1bbcb59f5714c6e4dc91aa5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636568"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="501ff-103">ExecNotificationQueryWmi 函式</span><span class="sxs-lookup"><span data-stu-id="501ff-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="501ff-104">執行查詢以接收事件。</span><span class="sxs-lookup"><span data-stu-id="501ff-104">Executes a query to receive events.</span></span> <span data-ttu-id="501ff-105">呼叫會立即傳回，並到達，呼叫端可以輪詢事件傳回的列舉值。</span><span class="sxs-lookup"><span data-stu-id="501ff-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="501ff-106">釋放傳回的列舉值會取消查詢。</span><span class="sxs-lookup"><span data-stu-id="501ff-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="501ff-107">語法</span><span class="sxs-lookup"><span data-stu-id="501ff-107">Syntax</span></span>

```cpp
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

## <a name="parameters"></a><span data-ttu-id="501ff-108">參數</span><span class="sxs-lookup"><span data-stu-id="501ff-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="501ff-109">[in]具有 Windows 管理所支援的有效的查詢語言的字串。</span><span class="sxs-lookup"><span data-stu-id="501ff-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="501ff-110">它必須是 < WQL >，WMI 查詢語言的縮寫字。</span><span class="sxs-lookup"><span data-stu-id="501ff-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="501ff-111">[in]查詢的文字。</span><span class="sxs-lookup"><span data-stu-id="501ff-111">[in] The text of the query.</span></span> <span data-ttu-id="501ff-112">這個參數不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="501ff-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="501ff-113">[in]下列兩個旗標會影響此函式行為的組合。</span><span class="sxs-lookup"><span data-stu-id="501ff-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="501ff-114">這些值會定義於*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。</span><span class="sxs-lookup"><span data-stu-id="501ff-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="501ff-115">常數</span><span class="sxs-lookup"><span data-stu-id="501ff-115">Constant</span></span> | <span data-ttu-id="501ff-116">值</span><span class="sxs-lookup"><span data-stu-id="501ff-116">Value</span></span>  | <span data-ttu-id="501ff-117">描述</span><span class="sxs-lookup"><span data-stu-id="501ff-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="501ff-118">0x10</span><span class="sxs-lookup"><span data-stu-id="501ff-118">0x10</span></span> | <span data-ttu-id="501ff-119">旗標會導致半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="501ff-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="501ff-120">如果未設定此旗標，則呼叫會失敗。</span><span class="sxs-lookup"><span data-stu-id="501ff-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="501ff-121">這是因為會持續收到的事件，這表示使用者必須輪詢傳回的列舉值。</span><span class="sxs-lookup"><span data-stu-id="501ff-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="501ff-122">無限期地封鎖此呼叫，可讓可在不可能。</span><span class="sxs-lookup"><span data-stu-id="501ff-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="501ff-123">0x20</span><span class="sxs-lookup"><span data-stu-id="501ff-123">0x20</span></span> | <span data-ttu-id="501ff-124">函數會傳回順向的列舉值。</span><span class="sxs-lookup"><span data-stu-id="501ff-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="501ff-125">一般而言，順向的列舉值會比較快，並使用較少的記憶體，比傳統的列舉值，但不是允許呼叫[複製品](clone.md)。</span><span class="sxs-lookup"><span data-stu-id="501ff-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="501ff-126">[in]一般而言，這個值是`null`。</span><span class="sxs-lookup"><span data-stu-id="501ff-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="501ff-127">否則，它是指標[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)可以提供所要求的事件提供者所使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="501ff-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="501ff-128">[out]如果未發生錯誤，接收列舉值，可讓呼叫端擷取查詢的結果集中的執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="501ff-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="501ff-129">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="501ff-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="501ff-130">[in]授權層級。</span><span class="sxs-lookup"><span data-stu-id="501ff-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="501ff-131">[in]模擬等級。</span><span class="sxs-lookup"><span data-stu-id="501ff-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="501ff-132">[in]指標[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件，表示目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="501ff-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="501ff-133">[in]使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="501ff-133">[in] The user name.</span></span> <span data-ttu-id="501ff-134">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="501ff-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="501ff-135">[in]密碼。</span><span class="sxs-lookup"><span data-stu-id="501ff-135">[in] The password.</span></span> <span data-ttu-id="501ff-136">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="501ff-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="501ff-137">[in]使用者的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="501ff-137">[in] The domain name of the user.</span></span> <span data-ttu-id="501ff-138">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="501ff-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="501ff-139">傳回值</span><span class="sxs-lookup"><span data-stu-id="501ff-139">Return value</span></span>

<span data-ttu-id="501ff-140">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="501ff-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="501ff-141">常數</span><span class="sxs-lookup"><span data-stu-id="501ff-141">Constant</span></span>  |<span data-ttu-id="501ff-142">值</span><span class="sxs-lookup"><span data-stu-id="501ff-142">Value</span></span>  |<span data-ttu-id="501ff-143">描述</span><span class="sxs-lookup"><span data-stu-id="501ff-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="501ff-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="501ff-144">0x80041003</span></span> | <span data-ttu-id="501ff-145">使用者沒有檢視一個或多個函式會傳回類別的權限。</span><span class="sxs-lookup"><span data-stu-id="501ff-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="501ff-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="501ff-146">0x80041001</span></span> | <span data-ttu-id="501ff-147">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="501ff-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="501ff-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="501ff-148">0x80041008</span></span> | <span data-ttu-id="501ff-149">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="501ff-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="501ff-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="501ff-150">0x80041010</span></span> | <span data-ttu-id="501ff-151">查詢指定了不存在的類別。</span><span class="sxs-lookup"><span data-stu-id="501ff-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="501ff-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="501ff-152">0x80042002</span></span> | <span data-ttu-id="501ff-153">已要求太多有效位數，傳遞的事件。</span><span class="sxs-lookup"><span data-stu-id="501ff-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="501ff-154">必須指定較大的輪詢容錯。</span><span class="sxs-lookup"><span data-stu-id="501ff-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="501ff-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="501ff-155">0x80042001</span></span> | <span data-ttu-id="501ff-156">查詢會要求 Windows 管理所無法提供的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="501ff-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="501ff-157">這`HRESULT`事件查詢會產生要輪詢的命名空間中的所有物件的要求時，會傳回。</span><span class="sxs-lookup"><span data-stu-id="501ff-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="501ff-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="501ff-158">0x80041017</span></span> | <span data-ttu-id="501ff-159">查詢必須有語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="501ff-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="501ff-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="501ff-160">0x80041018</span></span> | <span data-ttu-id="501ff-161">不支援要求的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="501ff-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="501ff-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="501ff-162">0x8004106c</span></span> | <span data-ttu-id="501ff-163">查詢太過複雜。</span><span class="sxs-lookup"><span data-stu-id="501ff-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="501ff-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="501ff-164">0x80041006</span></span> | <span data-ttu-id="501ff-165">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="501ff-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="501ff-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="501ff-166">0x80041033</span></span> | <span data-ttu-id="501ff-167">WMI 是可能已停止和重新啟動。</span><span class="sxs-lookup"><span data-stu-id="501ff-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="501ff-168">呼叫[ConnectServerWmi](connectserverwmi.md)一次。</span><span class="sxs-lookup"><span data-stu-id="501ff-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="501ff-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="501ff-169">0x80041015</span></span> | <span data-ttu-id="501ff-170">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="501ff-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="501ff-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="501ff-171">0x80041058</span></span> | <span data-ttu-id="501ff-172">無法剖析查詢。</span><span class="sxs-lookup"><span data-stu-id="501ff-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="501ff-173">0</span><span class="sxs-lookup"><span data-stu-id="501ff-173">0</span></span> | <span data-ttu-id="501ff-174">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="501ff-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="501ff-175">備註</span><span class="sxs-lookup"><span data-stu-id="501ff-175">Remarks</span></span>

<span data-ttu-id="501ff-176">此函式會包裝在呼叫[IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery)方法。</span><span class="sxs-lookup"><span data-stu-id="501ff-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="501ff-177">此函式傳回之後，呼叫端定期傳遞傳回`ppEnum`物件至[下一步](next.md)函式，以查看是否可以使用任何事件。</span><span class="sxs-lookup"><span data-stu-id="501ff-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="501ff-178">有一些限制的數目`AND`和`OR`可用在 WQL 查詢的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="501ff-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="501ff-179">大量複雜的查詢中所使用的 WQL 關鍵字可能會導致傳回 WMI `WBEM_E_QUOTA_VIOLATION` （或 0x8004106c） 做為錯誤碼`HRESULT`值。</span><span class="sxs-lookup"><span data-stu-id="501ff-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="501ff-180">複雜的查詢會視 WQL 關鍵字的限制。</span><span class="sxs-lookup"><span data-stu-id="501ff-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="501ff-181">如果函式呼叫失敗，您可以藉由呼叫來取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="501ff-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="501ff-182">需求</span><span class="sxs-lookup"><span data-stu-id="501ff-182">Requirements</span></span>

<span data-ttu-id="501ff-183">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="501ff-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="501ff-184">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="501ff-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="501ff-185">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="501ff-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="501ff-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="501ff-186">See also</span></span>

- [<span data-ttu-id="501ff-187">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="501ff-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
