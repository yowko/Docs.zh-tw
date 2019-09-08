---
title: ExecQueryWmi 函式（非受控 API 參考）
description: ExecQueryWmi 函數會執行查詢來抓取物件。
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8547d306819e85b838f1160d9912dd43e42f2f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798683"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="f307f-103">ExecQueryWmi 函式</span><span class="sxs-lookup"><span data-stu-id="f307f-103">ExecQueryWmi function</span></span>

<span data-ttu-id="f307f-104">執行查詢以擷取物件。</span><span class="sxs-lookup"><span data-stu-id="f307f-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f307f-105">語法</span><span class="sxs-lookup"><span data-stu-id="f307f-105">Syntax</span></span>

```cpp
HRESULT ExecQueryWmi (
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

## <a name="parameters"></a><span data-ttu-id="f307f-106">參數</span><span class="sxs-lookup"><span data-stu-id="f307f-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="f307f-107">在具有 Windows 管理支援之有效查詢語言的字串。</span><span class="sxs-lookup"><span data-stu-id="f307f-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="f307f-108">它必須是 "WQL"，也就是 WMI 查詢語言的縮寫。</span><span class="sxs-lookup"><span data-stu-id="f307f-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="f307f-109">在查詢的文字。</span><span class="sxs-lookup"><span data-stu-id="f307f-109">[in] The text of the query.</span></span> <span data-ttu-id="f307f-110">這個參數不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="f307f-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="f307f-111">在會影響此函式行為的旗標組合。</span><span class="sxs-lookup"><span data-stu-id="f307f-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="f307f-112">下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f307f-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="f307f-113">常數</span><span class="sxs-lookup"><span data-stu-id="f307f-113">Constant</span></span> | <span data-ttu-id="f307f-114">值</span><span class="sxs-lookup"><span data-stu-id="f307f-114">Value</span></span>  | <span data-ttu-id="f307f-115">描述</span><span class="sxs-lookup"><span data-stu-id="f307f-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="f307f-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="f307f-116">0x20000</span></span> | <span data-ttu-id="f307f-117">如果設定，函式會抓取已修改的限定詞，並儲存在目前連接地區設定的當地語系化命名空間中。</span><span class="sxs-lookup"><span data-stu-id="f307f-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="f307f-118">如果未設定，此函式只會抓取立即命名空間中儲存的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f307f-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="f307f-119">0x10</span><span class="sxs-lookup"><span data-stu-id="f307f-119">0x10</span></span> | <span data-ttu-id="f307f-120">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="f307f-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="f307f-121">0x20</span><span class="sxs-lookup"><span data-stu-id="f307f-121">0x20</span></span> | <span data-ttu-id="f307f-122">函數會傳回順向列舉值。</span><span class="sxs-lookup"><span data-stu-id="f307f-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="f307f-123">一般來說，順向列舉值的速度較快，而且使用的記憶體比傳統的列舉值少，但它們不允許[複製](clone.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f307f-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="f307f-124">0</span><span class="sxs-lookup"><span data-stu-id="f307f-124">0</span></span> | <span data-ttu-id="f307f-125">WMI 會保留列舉中物件的指標，直到釋放它們為止。</span><span class="sxs-lookup"><span data-stu-id="f307f-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="f307f-126">0x100</span><span class="sxs-lookup"><span data-stu-id="f307f-126">0x100</span></span> | <span data-ttu-id="f307f-127">確保任何傳回的物件都有足夠的資訊，因此系統屬性（例如 **__PATH**、 **__RELPATH**和 **__SERVER**）不`null`會。</span><span class="sxs-lookup"><span data-stu-id="f307f-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="f307f-128">2</span><span class="sxs-lookup"><span data-stu-id="f307f-128">2</span></span> | <span data-ttu-id="f307f-129">此旗標用於原型設計。</span><span class="sxs-lookup"><span data-stu-id="f307f-129">This flag is used for prototyping.</span></span> <span data-ttu-id="f307f-130">它不會執行查詢，而是會傳回看起來像一般結果物件的物件。</span><span class="sxs-lookup"><span data-stu-id="f307f-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="f307f-131">0x200</span><span class="sxs-lookup"><span data-stu-id="f307f-131">0x200</span></span> | <span data-ttu-id="f307f-132">會針對指定的類別直接存取提供者，而不考慮其父類別或任何子類別。</span><span class="sxs-lookup"><span data-stu-id="f307f-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="f307f-133">建議的旗標`WBEM_FLAG_RETURN_IMMEDIATELY`為`WBEM_FLAG_FORWARD_ONLY` ，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="f307f-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="f307f-134">在通常，此值為`null`。</span><span class="sxs-lookup"><span data-stu-id="f307f-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="f307f-135">否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="f307f-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="f307f-136">脫銷如果沒有發生錯誤，則會接收列舉值的指標，允許呼叫者抓取查詢結果集中的實例。</span><span class="sxs-lookup"><span data-stu-id="f307f-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="f307f-137">查詢的結果集可以有零個實例。</span><span class="sxs-lookup"><span data-stu-id="f307f-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="f307f-138">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="f307f-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="f307f-139">在授權層級。</span><span class="sxs-lookup"><span data-stu-id="f307f-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="f307f-140">在模擬層級。</span><span class="sxs-lookup"><span data-stu-id="f307f-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="f307f-141">在[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件的指標，表示目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f307f-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="f307f-142">在使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f307f-142">[in] The user name.</span></span> <span data-ttu-id="f307f-143">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f307f-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="f307f-144">在密碼。</span><span class="sxs-lookup"><span data-stu-id="f307f-144">[in] The password.</span></span> <span data-ttu-id="f307f-145">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f307f-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="f307f-146">在使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="f307f-146">[in] The domain name of the user.</span></span> <span data-ttu-id="f307f-147">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f307f-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="f307f-148">傳回值</span><span class="sxs-lookup"><span data-stu-id="f307f-148">Return value</span></span>

<span data-ttu-id="f307f-149">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f307f-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f307f-150">常數</span><span class="sxs-lookup"><span data-stu-id="f307f-150">Constant</span></span>  |<span data-ttu-id="f307f-151">值</span><span class="sxs-lookup"><span data-stu-id="f307f-151">Value</span></span>  |<span data-ttu-id="f307f-152">說明</span><span class="sxs-lookup"><span data-stu-id="f307f-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="f307f-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="f307f-153">0x80041003</span></span> | <span data-ttu-id="f307f-154">使用者沒有許可權可查看函數可以傳回的一個或多個類別。</span><span class="sxs-lookup"><span data-stu-id="f307f-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="f307f-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f307f-155">0x80041001</span></span> | <span data-ttu-id="f307f-156">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f307f-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f307f-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f307f-157">0x80041008</span></span> | <span data-ttu-id="f307f-158">參數無效。</span><span class="sxs-lookup"><span data-stu-id="f307f-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="f307f-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="f307f-159">0x80041017</span></span> | <span data-ttu-id="f307f-160">查詢發生語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="f307f-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="f307f-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="f307f-161">0x80041018</span></span> | <span data-ttu-id="f307f-162">不支援要求的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="f307f-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="f307f-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="f307f-163">0x8004106c</span></span> | <span data-ttu-id="f307f-164">查詢太複雜。</span><span class="sxs-lookup"><span data-stu-id="f307f-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f307f-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f307f-165">0x80041006</span></span> | <span data-ttu-id="f307f-166">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="f307f-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="f307f-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="f307f-167">0x80041033</span></span> | <span data-ttu-id="f307f-168">WMI 可能已停止並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="f307f-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="f307f-169">再次呼叫[ConnectServerWmi](connectserverwmi.md) 。</span><span class="sxs-lookup"><span data-stu-id="f307f-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f307f-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f307f-170">0x80041015</span></span> | <span data-ttu-id="f307f-171">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="f307f-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f307f-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f307f-172">0x80041002</span></span> | <span data-ttu-id="f307f-173">查詢指定了不存在的類別。</span><span class="sxs-lookup"><span data-stu-id="f307f-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f307f-174">0</span><span class="sxs-lookup"><span data-stu-id="f307f-174">0</span></span> | <span data-ttu-id="f307f-175">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f307f-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f307f-176">備註</span><span class="sxs-lookup"><span data-stu-id="f307f-176">Remarks</span></span>

<span data-ttu-id="f307f-177">此函式會包裝對[IWbemServices：： ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f307f-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="f307f-178">此函式會處理`strQuery`參數中指定的查詢，並建立可供呼叫端用來存取查詢結果的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f307f-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="f307f-179">列舉值是指向[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)介面的指標;查詢結果是透過[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)介面提供之類別物件的實例。</span><span class="sxs-lookup"><span data-stu-id="f307f-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="f307f-180">可以在 WQL 查詢中使用的`AND`和`OR`關鍵字數目有所限制。</span><span class="sxs-lookup"><span data-stu-id="f307f-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="f307f-181">複雜查詢中使用的大量 WQL 關鍵字可能會使 WMI `WBEM_E_QUOTA_VIOLATION`傳回（或0x8004106c）錯誤碼`HRESULT`做為值。</span><span class="sxs-lookup"><span data-stu-id="f307f-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="f307f-182">WQL 關鍵字的限制取決於查詢的複雜程度。</span><span class="sxs-lookup"><span data-stu-id="f307f-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="f307f-183">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="f307f-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f307f-184">需求</span><span class="sxs-lookup"><span data-stu-id="f307f-184">Requirements</span></span>

<span data-ttu-id="f307f-185">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f307f-185">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f307f-186">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f307f-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="f307f-187">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f307f-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f307f-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f307f-188">See also</span></span>

- [<span data-ttu-id="f307f-189">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="f307f-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
