---
title: "ExecQueryWmi 函式 （Unmanaged API 參考）"
description: "ExecQueryWmi 函式會執行查詢以擷取物件。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecQueryWmi
helpviewer_keywords: ExecQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 872109cb0472a8404c492c2867429fe783f898eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="execquerywmi-function"></a><span data-ttu-id="349cd-103">ExecQueryWmi 函式</span><span class="sxs-lookup"><span data-stu-id="349cd-103">ExecQueryWmi function</span></span>
<span data-ttu-id="349cd-104">執行查詢以擷取物件。</span><span class="sxs-lookup"><span data-stu-id="349cd-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="349cd-105">語法</span><span class="sxs-lookup"><span data-stu-id="349cd-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="349cd-106">參數</span><span class="sxs-lookup"><span data-stu-id="349cd-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="349cd-107">[in]具有 Windows 管理所支援的有效的查詢語言的字串。</span><span class="sxs-lookup"><span data-stu-id="349cd-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="349cd-108">它必須是"WQL，「 WMI 查詢語言的縮寫。</span><span class="sxs-lookup"><span data-stu-id="349cd-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="349cd-109">[in]查詢的文字。</span><span class="sxs-lookup"><span data-stu-id="349cd-109">[in] The text of the query.</span></span> <span data-ttu-id="349cd-110">此參數不得為`null`。</span><span class="sxs-lookup"><span data-stu-id="349cd-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="349cd-111">[in]影響此函式的行為的旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="349cd-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="349cd-112">下列的值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="349cd-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="349cd-113">常數</span><span class="sxs-lookup"><span data-stu-id="349cd-113">Constant</span></span> | <span data-ttu-id="349cd-114">值</span><span class="sxs-lookup"><span data-stu-id="349cd-114">Value</span></span>  | <span data-ttu-id="349cd-115">描述</span><span class="sxs-lookup"><span data-stu-id="349cd-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="349cd-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="349cd-116">0x20000</span></span> | <span data-ttu-id="349cd-117">如果集合，此函式會擷取目前連接的地區設定當地語系化的命名空間中儲存已修改的限定詞。</span><span class="sxs-lookup"><span data-stu-id="349cd-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="349cd-118">如果未設定，此函數會擷取只儲存立即命名空間中的限定詞。</span><span class="sxs-lookup"><span data-stu-id="349cd-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="349cd-119">0x10</span><span class="sxs-lookup"><span data-stu-id="349cd-119">0x10</span></span> | <span data-ttu-id="349cd-120">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="349cd-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="349cd-121">0x20</span><span class="sxs-lookup"><span data-stu-id="349cd-121">0x20</span></span> | <span data-ttu-id="349cd-122">函數會傳回順向的列舉值。</span><span class="sxs-lookup"><span data-stu-id="349cd-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="349cd-123">一般而言，順向的列舉程式會更快，並使用較少的記憶體比傳統的列舉值，但不是允許呼叫[複製](clone.md)。</span><span class="sxs-lookup"><span data-stu-id="349cd-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="349cd-124">0</span><span class="sxs-lookup"><span data-stu-id="349cd-124">0</span></span> | <span data-ttu-id="349cd-125">WMI 會保留 enumration 中物件的指標，直到釋放為止。</span><span class="sxs-lookup"><span data-stu-id="349cd-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="349cd-126">0x100</span><span class="sxs-lookup"><span data-stu-id="349cd-126">0x100</span></span> | <span data-ttu-id="349cd-127">任何傳回的物件會有足夠的資訊在其中因此可確保該系統屬性，例如**__PATH**， **__RELPATH**，和**GET-WMIOBJECT**，不是`null`。</span><span class="sxs-lookup"><span data-stu-id="349cd-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="349cd-128">2</span><span class="sxs-lookup"><span data-stu-id="349cd-128">2</span></span> | <span data-ttu-id="349cd-129">這個旗標用於建立原型。</span><span class="sxs-lookup"><span data-stu-id="349cd-129">This flag is used for prototyping.</span></span> <span data-ttu-id="349cd-130">它不會執行查詢，並改為傳回看起來像一般的結果物件的物件。</span><span class="sxs-lookup"><span data-stu-id="349cd-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="349cd-131">0x200</span><span class="sxs-lookup"><span data-stu-id="349cd-131">0x200</span></span> | <span data-ttu-id="349cd-132">原因直接存取提供者的指定，而不考慮其父類別或任何子類別的類別。</span><span class="sxs-lookup"><span data-stu-id="349cd-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="349cd-133">建議的旗標是`WBEM_FLAG_RETURN_IMMEDIATELY`和`WBEM_FLAG_FORWARD_ONLY`為了達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="349cd-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="349cd-134">[in]一般而言，這個值是`null`。</span><span class="sxs-lookup"><span data-stu-id="349cd-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="349cd-135">否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可用的提供者所提供的要求的類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="349cd-135">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="349cd-136">[out]如果沒有發生錯誤，接收列舉值，可讓呼叫端擷取在查詢的結果集的執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="349cd-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="349cd-137">查詢可以有零個執行個體具有結果集。</span><span class="sxs-lookup"><span data-stu-id="349cd-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="349cd-138">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="349cd-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="349cd-139">[in]授權層級。</span><span class="sxs-lookup"><span data-stu-id="349cd-139">[in] The authorization level.</span></span>

<span data-ttu-id="349cd-140">`impLevel`[in]模擬等級。</span><span class="sxs-lookup"><span data-stu-id="349cd-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="349cd-141">[in]指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)物件，代表目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="349cd-141">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="349cd-142">[in]使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="349cd-142">[in] The user name.</span></span> <span data-ttu-id="349cd-143">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="349cd-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="349cd-144">[in]密碼。</span><span class="sxs-lookup"><span data-stu-id="349cd-144">[in] The password.</span></span> <span data-ttu-id="349cd-145">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="349cd-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="349cd-146">[in]使用者的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="349cd-146">[in] The domain name of the user.</span></span> <span data-ttu-id="349cd-147">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="349cd-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="349cd-148">傳回值</span><span class="sxs-lookup"><span data-stu-id="349cd-148">Return value</span></span>

<span data-ttu-id="349cd-149">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="349cd-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="349cd-150">常數</span><span class="sxs-lookup"><span data-stu-id="349cd-150">Constant</span></span>  |<span data-ttu-id="349cd-151">值</span><span class="sxs-lookup"><span data-stu-id="349cd-151">Value</span></span>  |<span data-ttu-id="349cd-152">描述</span><span class="sxs-lookup"><span data-stu-id="349cd-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="349cd-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="349cd-153">0x80041003</span></span> | <span data-ttu-id="349cd-154">使用者沒有檢視一或多個函式可以傳回的類別權限。</span><span class="sxs-lookup"><span data-stu-id="349cd-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="349cd-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="349cd-155">0x80041001</span></span> | <span data-ttu-id="349cd-156">發生意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="349cd-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="349cd-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="349cd-157">0x80041008</span></span> | <span data-ttu-id="349cd-158">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="349cd-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="349cd-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="349cd-159">0x80041017</span></span> | <span data-ttu-id="349cd-160">查詢中有語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="349cd-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="349cd-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="349cd-161">0x80041018</span></span> | <span data-ttu-id="349cd-162">不支援要求的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="349cd-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="349cd-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="349cd-163">0x8004106c</span></span> | <span data-ttu-id="349cd-164">查詢太過複雜。</span><span class="sxs-lookup"><span data-stu-id="349cd-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="349cd-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="349cd-165">0x80041006</span></span> | <span data-ttu-id="349cd-166">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="349cd-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="349cd-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="349cd-167">0x80041033</span></span> | <span data-ttu-id="349cd-168">WMI 是可能已停止和重新啟動。</span><span class="sxs-lookup"><span data-stu-id="349cd-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="349cd-169">呼叫[ConnectServerWmi](connectserverwmi.md)一次。</span><span class="sxs-lookup"><span data-stu-id="349cd-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="349cd-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="349cd-170">0x80041015</span></span> | <span data-ttu-id="349cd-171">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="349cd-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="349cd-172">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="349cd-172">0x80041002</span></span> | <span data-ttu-id="349cd-173">查詢會指定不存在的類別。</span><span class="sxs-lookup"><span data-stu-id="349cd-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="349cd-174">0</span><span class="sxs-lookup"><span data-stu-id="349cd-174">0</span></span> | <span data-ttu-id="349cd-175">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="349cd-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="349cd-176">備註</span><span class="sxs-lookup"><span data-stu-id="349cd-176">Remarks</span></span>

<span data-ttu-id="349cd-177">此函式會包裝呼叫[IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="349cd-177">This function wraps a call to the [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="349cd-178">此函式會處理查詢中指定`strQuery`參數，並建立呼叫者可以透過它存取查詢結果的列舉值。</span><span class="sxs-lookup"><span data-stu-id="349cd-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="349cd-179">列舉值是指標[IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx)介面; 查詢結果就是執行個體類別物件可透過[IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx)介面。</span><span class="sxs-lookup"><span data-stu-id="349cd-179">The enumerator is a pointer to an [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; the query results are instances of class objects made available through the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span></span>

<span data-ttu-id="349cd-180">限制數目`AND`和`OR`可以在 WQL 查詢中使用的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="349cd-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="349cd-181">大量的複雜查詢中使用的 WQL 關鍵字可能會導致 WMI 傳回`WBEM_E_QUOTA_VIOLATION`（或 0x8004106c） 錯誤的程式碼做為`HRESULT`值。</span><span class="sxs-lookup"><span data-stu-id="349cd-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="349cd-182">多複雜的查詢是取決於 WQL 關鍵字的限制。</span><span class="sxs-lookup"><span data-stu-id="349cd-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="349cd-183">如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="349cd-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="349cd-184">需求</span><span class="sxs-lookup"><span data-stu-id="349cd-184">Requirements</span></span>  
 <span data-ttu-id="349cd-185">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="349cd-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="349cd-186">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="349cd-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="349cd-187">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="349cd-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349cd-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="349cd-188">See also</span></span>  
[<span data-ttu-id="349cd-189">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="349cd-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
