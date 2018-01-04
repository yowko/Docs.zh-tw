---
title: "CreateInstanceEnumWmi 函式 （Unmanaged API 參考）"
description: "CreateInstanceEnumWmi 函式會傳回包含指定的類別符合選取準則的執行個體的列舉值。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateInstanceEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateInstanceEnumWmi
helpviewer_keywords: CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b796771b07dee28470d37ca3e4292c0a244e056b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="56fc8-103">CreateInstanceEnumWmi 函式</span><span class="sxs-lookup"><span data-stu-id="56fc8-103">CreateInstanceEnumWmi function</span></span>
<span data-ttu-id="56fc8-104">傳回列舉值，會傳回符合指定的選取準則指定類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56fc8-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="56fc8-105">語法</span><span class="sxs-lookup"><span data-stu-id="56fc8-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="56fc8-106">參數</span><span class="sxs-lookup"><span data-stu-id="56fc8-106">Parameters</span></span>

`strFilter`    
<span data-ttu-id="56fc8-107">[in]類別想要與執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fc8-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="56fc8-108">此參數不得為`null`。</span><span class="sxs-lookup"><span data-stu-id="56fc8-108">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="56fc8-109">[in]影響此函式的行為的旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="56fc8-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="56fc8-110">下列的值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="56fc8-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="56fc8-111">常數</span><span class="sxs-lookup"><span data-stu-id="56fc8-111">Constant</span></span>  |<span data-ttu-id="56fc8-112">值</span><span class="sxs-lookup"><span data-stu-id="56fc8-112">Value</span></span>  |<span data-ttu-id="56fc8-113">描述</span><span class="sxs-lookup"><span data-stu-id="56fc8-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="56fc8-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="56fc8-114">0x20000</span></span> | <span data-ttu-id="56fc8-115">如果集合，此函式會擷取目前連接的地區設定當地語系化的命名空間中儲存已修改的限定詞。</span><span class="sxs-lookup"><span data-stu-id="56fc8-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="56fc8-116">如果未設定，此函數會擷取只儲存立即命名空間中的限定詞。</span><span class="sxs-lookup"><span data-stu-id="56fc8-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="56fc8-117">0</span><span class="sxs-lookup"><span data-stu-id="56fc8-117">0</span></span> | <span data-ttu-id="56fc8-118">列舉會包含這和所有子類別階層架構中。</span><span class="sxs-lookup"><span data-stu-id="56fc8-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="56fc8-119">1</span><span class="sxs-lookup"><span data-stu-id="56fc8-119">1</span></span> | <span data-ttu-id="56fc8-120">列舉包含這個類別只能純粹執行個體，但不包括提供此類別中找不到屬性的子類別的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="56fc8-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="56fc8-121">0x10</span><span class="sxs-lookup"><span data-stu-id="56fc8-121">0x10</span></span> | <span data-ttu-id="56fc8-122">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="56fc8-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="56fc8-123">0x20</span><span class="sxs-lookup"><span data-stu-id="56fc8-123">0x20</span></span> | <span data-ttu-id="56fc8-124">函數會傳回順向的列舉值。</span><span class="sxs-lookup"><span data-stu-id="56fc8-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="56fc8-125">一般而言，順向的列舉程式會更快，並使用較少的記憶體比傳統的列舉值，但不是允許呼叫[複製](clone.md)。</span><span class="sxs-lookup"><span data-stu-id="56fc8-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="56fc8-126">0</span><span class="sxs-lookup"><span data-stu-id="56fc8-126">0</span></span> | <span data-ttu-id="56fc8-127">WMI 會保留 enumration 中物件的指標，直到釋放為止。</span><span class="sxs-lookup"><span data-stu-id="56fc8-127">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="56fc8-128">建議的旗標是`WBEM_FLAG_RETURN_IMMEDIATELY`和`WBEM_FLAG_FORWARD_ONLY`為了達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="56fc8-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="56fc8-129">[in]一般而言，這個值是`null`。</span><span class="sxs-lookup"><span data-stu-id="56fc8-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="56fc8-130">否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可能使用的提供者所提供要求的執行個體的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56fc8-130">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`  
<span data-ttu-id="56fc8-131">[out]接收列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="56fc8-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="56fc8-132">[in]授權層級。</span><span class="sxs-lookup"><span data-stu-id="56fc8-132">[in] The authorization level.</span></span>

<span data-ttu-id="56fc8-133">`impLevel`[in]模擬等級。</span><span class="sxs-lookup"><span data-stu-id="56fc8-133">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="56fc8-134">[in]指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)物件，代表目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="56fc8-134">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="56fc8-135">[in]使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="56fc8-135">[in] The user name.</span></span> <span data-ttu-id="56fc8-136">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="56fc8-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="56fc8-137">[in]密碼。</span><span class="sxs-lookup"><span data-stu-id="56fc8-137">[in] The password.</span></span> <span data-ttu-id="56fc8-138">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="56fc8-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="56fc8-139">[in]使用者的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="56fc8-139">[in] The domain name of the user.</span></span> <span data-ttu-id="56fc8-140">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="56fc8-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="56fc8-141">傳回值</span><span class="sxs-lookup"><span data-stu-id="56fc8-141">Return value</span></span>

<span data-ttu-id="56fc8-142">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="56fc8-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="56fc8-143">常數</span><span class="sxs-lookup"><span data-stu-id="56fc8-143">Constant</span></span>  |<span data-ttu-id="56fc8-144">值</span><span class="sxs-lookup"><span data-stu-id="56fc8-144">Value</span></span>  |<span data-ttu-id="56fc8-145">描述</span><span class="sxs-lookup"><span data-stu-id="56fc8-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="56fc8-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="56fc8-146">0x80041003</span></span> | <span data-ttu-id="56fc8-147">使用者沒有權限來檢視指定之類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56fc8-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="56fc8-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="56fc8-148">0x80041001</span></span> | <span data-ttu-id="56fc8-149">發生意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="56fc8-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="56fc8-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="56fc8-150">0x80041010</span></span> | <span data-ttu-id="56fc8-151">`strFilter` 不存在。</span><span class="sxs-lookup"><span data-stu-id="56fc8-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="56fc8-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="56fc8-152">0x80041008</span></span> | <span data-ttu-id="56fc8-153">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="56fc8-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="56fc8-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="56fc8-154">0x80041006</span></span> | <span data-ttu-id="56fc8-155">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="56fc8-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="56fc8-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="56fc8-156">0x80041033</span></span> | <span data-ttu-id="56fc8-157">WMI 是可能已停止和重新啟動。</span><span class="sxs-lookup"><span data-stu-id="56fc8-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="56fc8-158">呼叫[ConnectServerWmi](connectserverwmi.md)一次。</span><span class="sxs-lookup"><span data-stu-id="56fc8-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="56fc8-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="56fc8-159">0x80041015</span></span> | <span data-ttu-id="56fc8-160">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="56fc8-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="56fc8-161">0</span><span class="sxs-lookup"><span data-stu-id="56fc8-161">0</span></span> | <span data-ttu-id="56fc8-162">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="56fc8-162">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="56fc8-163">備註</span><span class="sxs-lookup"><span data-stu-id="56fc8-163">Remarks</span></span>

<span data-ttu-id="56fc8-164">此函式會包裝呼叫[iwbemservices:: Createclassenum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="56fc8-164">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="56fc8-165">請注意傳回的列舉值可以有零個元素。</span><span class="sxs-lookup"><span data-stu-id="56fc8-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="56fc8-166">如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="56fc8-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="56fc8-167">需求</span><span class="sxs-lookup"><span data-stu-id="56fc8-167">Requirements</span></span>  
 <span data-ttu-id="56fc8-168">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56fc8-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fc8-169">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="56fc8-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="56fc8-170">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="56fc8-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fc8-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56fc8-171">See also</span></span>  
[<span data-ttu-id="56fc8-172">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="56fc8-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
