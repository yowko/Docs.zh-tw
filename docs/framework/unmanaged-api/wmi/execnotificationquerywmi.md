---
title: ExecNotificationQueryWmi 函式（非受控 API 參考）
description: ExecNotificationQueryWmi 函數會執行查詢來接收事件。
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
ms.openlocfilehash: 5cfe54c7c9b7ae707b2d3591afbd830bac171f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798640"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="fd7f3-103">ExecNotificationQueryWmi 函式</span><span class="sxs-lookup"><span data-stu-id="fd7f3-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="fd7f3-104">執行查詢以接收事件。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-104">Executes a query to receive events.</span></span> <span data-ttu-id="fd7f3-105">此呼叫會立即傳回，而且呼叫端可以在事件抵達時輪詢傳回的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="fd7f3-106">釋放傳回的列舉值會取消查詢。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="fd7f3-107">語法</span><span class="sxs-lookup"><span data-stu-id="fd7f3-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="fd7f3-108">參數</span><span class="sxs-lookup"><span data-stu-id="fd7f3-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="fd7f3-109">在具有 Windows 管理支援之有效查詢語言的字串。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="fd7f3-110">它必須是 "WQL"，也就是 WMI 查詢語言的縮寫。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="fd7f3-111">在查詢的文字。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-111">[in] The text of the query.</span></span> <span data-ttu-id="fd7f3-112">這個參數不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="fd7f3-113">在下列兩個旗標的組合，會影響此函式的行為。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="fd7f3-114">這些值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="fd7f3-115">常數</span><span class="sxs-lookup"><span data-stu-id="fd7f3-115">Constant</span></span> | <span data-ttu-id="fd7f3-116">值</span><span class="sxs-lookup"><span data-stu-id="fd7f3-116">Value</span></span>  | <span data-ttu-id="fd7f3-117">描述</span><span class="sxs-lookup"><span data-stu-id="fd7f3-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="fd7f3-118">0x10</span><span class="sxs-lookup"><span data-stu-id="fd7f3-118">0x10</span></span> | <span data-ttu-id="fd7f3-119">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="fd7f3-120">如果未設定此旗標，呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="fd7f3-121">這是因為系統會持續收到事件，這表示使用者必須輪詢傳回的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="fd7f3-122">無限期地封鎖此呼叫會導致無法這麼做。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="fd7f3-123">0x20</span><span class="sxs-lookup"><span data-stu-id="fd7f3-123">0x20</span></span> | <span data-ttu-id="fd7f3-124">函數會傳回順向列舉值。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="fd7f3-125">一般來說，順向列舉值的速度較快，而且使用的記憶體比傳統的列舉值少，但它們不允許[複製](clone.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="fd7f3-126">在通常，此值為`null`。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="fd7f3-127">否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求事件的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="fd7f3-128">脫銷如果沒有發生錯誤，則會接收列舉值的指標，允許呼叫者抓取查詢結果集中的實例。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="fd7f3-129">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="fd7f3-130">在授權層級。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="fd7f3-131">在模擬層級。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="fd7f3-132">在[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件的指標，表示目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="fd7f3-133">在使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-133">[in] The user name.</span></span> <span data-ttu-id="fd7f3-134">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="fd7f3-135">在密碼。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-135">[in] The password.</span></span> <span data-ttu-id="fd7f3-136">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="fd7f3-137">在使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-137">[in] The domain name of the user.</span></span> <span data-ttu-id="fd7f3-138">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="fd7f3-139">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd7f3-139">Return value</span></span>

<span data-ttu-id="fd7f3-140">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="fd7f3-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fd7f3-141">常數</span><span class="sxs-lookup"><span data-stu-id="fd7f3-141">Constant</span></span>  |<span data-ttu-id="fd7f3-142">值</span><span class="sxs-lookup"><span data-stu-id="fd7f3-142">Value</span></span>  |<span data-ttu-id="fd7f3-143">描述</span><span class="sxs-lookup"><span data-stu-id="fd7f3-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="fd7f3-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="fd7f3-144">0x80041003</span></span> | <span data-ttu-id="fd7f3-145">使用者沒有許可權可查看函數可以傳回的一個或多個類別。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="fd7f3-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="fd7f3-146">0x80041001</span></span> | <span data-ttu-id="fd7f3-147">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fd7f3-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fd7f3-148">0x80041008</span></span> | <span data-ttu-id="fd7f3-149">參數無效。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="fd7f3-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="fd7f3-150">0x80041010</span></span> | <span data-ttu-id="fd7f3-151">查詢指定了不存在的類別。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="fd7f3-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="fd7f3-152">0x80042002</span></span> | <span data-ttu-id="fd7f3-153">要求傳遞事件的精確度太高。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="fd7f3-154">必須指定較大的輪詢容錯。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="fd7f3-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="fd7f3-155">0x80042001</span></span> | <span data-ttu-id="fd7f3-156">查詢要求的資訊比 Windows 管理所能提供的還要多。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="fd7f3-157">當`HRESULT`事件查詢產生輪詢命名空間中所有物件的要求時，就會傳回此專案。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="fd7f3-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="fd7f3-158">0x80041017</span></span> | <span data-ttu-id="fd7f3-159">查詢發生語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="fd7f3-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="fd7f3-160">0x80041018</span></span> | <span data-ttu-id="fd7f3-161">不支援要求的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="fd7f3-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="fd7f3-162">0x8004106c</span></span> | <span data-ttu-id="fd7f3-163">查詢太複雜。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="fd7f3-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="fd7f3-164">0x80041006</span></span> | <span data-ttu-id="fd7f3-165">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="fd7f3-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="fd7f3-166">0x80041033</span></span> | <span data-ttu-id="fd7f3-167">WMI 可能已停止並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="fd7f3-168">再次呼叫[ConnectServerWmi](connectserverwmi.md) 。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="fd7f3-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="fd7f3-169">0x80041015</span></span> | <span data-ttu-id="fd7f3-170">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="fd7f3-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="fd7f3-171">0x80041058</span></span> | <span data-ttu-id="fd7f3-172">無法剖析查詢。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="fd7f3-173">0</span><span class="sxs-lookup"><span data-stu-id="fd7f3-173">0</span></span> | <span data-ttu-id="fd7f3-174">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="fd7f3-175">備註</span><span class="sxs-lookup"><span data-stu-id="fd7f3-175">Remarks</span></span>

<span data-ttu-id="fd7f3-176">此函式會包裝對[IWbemServices：： ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="fd7f3-177">函式傳回之後，呼叫端會定期將傳回`ppEnum`的物件傳遞至[下一個](next.md)函式，以查看是否有任何可用的事件。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="fd7f3-178">可以在 WQL 查詢中使用的`AND`和`OR`關鍵字數目有所限制。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="fd7f3-179">複雜查詢中使用的大量 WQL 關鍵字可能會使 WMI `WBEM_E_QUOTA_VIOLATION`傳回（或0x8004106c）錯誤碼`HRESULT`做為值。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="fd7f3-180">WQL 關鍵字的限制取決於查詢的複雜程度。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="fd7f3-181">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd7f3-182">需求</span><span class="sxs-lookup"><span data-stu-id="fd7f3-182">Requirements</span></span>

<span data-ttu-id="fd7f3-183">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd7f3-183">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="fd7f3-184">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fd7f3-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="fd7f3-185">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fd7f3-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fd7f3-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd7f3-186">See also</span></span>

- [<span data-ttu-id="fd7f3-187">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="fd7f3-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
