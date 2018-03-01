---
title: "CreateClassEnumWmi 函式 （Unmanaged API 參考）"
description: "CreateClassEnumWmi 函式會傳回符合指定的條件的所有類別的列舉值。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2058bad61af79244d211afb6a7661ca1642db070
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="4f5a8-103">CreateClassEnumWmi 函式</span><span class="sxs-lookup"><span data-stu-id="4f5a8-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="4f5a8-104">傳回符合指定的選取準則的所有類別的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4f5a8-105">語法</span><span class="sxs-lookup"><span data-stu-id="4f5a8-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="4f5a8-106">參數</span><span class="sxs-lookup"><span data-stu-id="4f5a8-106">Parameters</span></span>

`strSuperclass`    
<span data-ttu-id="4f5a8-107">[in]如果沒有`null`或空白，會指定父類別名稱; 此列舉值傳回此類別的子類別。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="4f5a8-108">如果是`null`或空白和`lFlags`WBEM_FLAG_SHALLOW，傳回最上層類別 （類別沒有父類別）。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="4f5a8-109">如果是`null`或空白和`lFlags`是`WBEM_FLAG_DEEP`，傳回命名空間中的所有類別。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`   
<span data-ttu-id="4f5a8-110">[in]影響此函式的行為的旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="4f5a8-111">下列的值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="4f5a8-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="4f5a8-112">常數</span><span class="sxs-lookup"><span data-stu-id="4f5a8-112">Constant</span></span>  |<span data-ttu-id="4f5a8-113">值</span><span class="sxs-lookup"><span data-stu-id="4f5a8-113">Value</span></span>  |<span data-ttu-id="4f5a8-114">描述</span><span class="sxs-lookup"><span data-stu-id="4f5a8-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="4f5a8-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="4f5a8-115">0x20000</span></span> | <span data-ttu-id="4f5a8-116">如果集合，此函式會擷取目前連接的地區設定當地語系化的命名空間中儲存已修改的限定詞。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="4f5a8-117">如果未設定，此函數會擷取只儲存立即命名空間中的限定詞。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="4f5a8-118">0</span><span class="sxs-lookup"><span data-stu-id="4f5a8-118">0</span></span> | <span data-ttu-id="4f5a8-119">列舉型別階層架構，但不是此類別包含所有子類別。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="4f5a8-120">1</span><span class="sxs-lookup"><span data-stu-id="4f5a8-120">1</span></span> | <span data-ttu-id="4f5a8-121">列舉包含這個類別只能純粹執行個體，但不包括提供此類別中找不到屬性的子類別的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="4f5a8-122">0x10</span><span class="sxs-lookup"><span data-stu-id="4f5a8-122">0x10</span></span> | <span data-ttu-id="4f5a8-123">旗標會造成半同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="4f5a8-124">0x20</span><span class="sxs-lookup"><span data-stu-id="4f5a8-124">0x20</span></span> | <span data-ttu-id="4f5a8-125">函數會傳回順向的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="4f5a8-126">一般而言，順向的列舉程式會更快，並使用較少的記憶體比傳統的列舉值，但不是允許呼叫[複製](clone.md)。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="4f5a8-127">0</span><span class="sxs-lookup"><span data-stu-id="4f5a8-127">0</span></span> | <span data-ttu-id="4f5a8-128">WMI 會保留 enumration 中物件的指標，直到釋放為止。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-128">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="4f5a8-129">建議的旗標是`WBEM_FLAG_RETURN_IMMEDIATELY`和`WBEM_FLAG_FORWARD_ONLY`為了達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="4f5a8-130">[in]一般而言，這個值是`null`。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="4f5a8-131">否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可用的提供者所提供的要求的類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-131">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="4f5a8-132">[out]接收列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="4f5a8-133">[in]授權層級。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-133">[in] The authorization level.</span></span>

<span data-ttu-id="4f5a8-134">`impLevel`[in]模擬等級。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-134">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="4f5a8-135">[in]指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)物件，代表目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-135">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="4f5a8-136">[in]使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-136">[in] The user name.</span></span> <span data-ttu-id="4f5a8-137">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="4f5a8-138">[in]密碼。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-138">[in] The password.</span></span> <span data-ttu-id="4f5a8-139">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="4f5a8-140">[in]使用者的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-140">[in] The domain name of the user.</span></span> <span data-ttu-id="4f5a8-141">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="4f5a8-142">傳回值</span><span class="sxs-lookup"><span data-stu-id="4f5a8-142">Return value</span></span>

<span data-ttu-id="4f5a8-143">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="4f5a8-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4f5a8-144">常數</span><span class="sxs-lookup"><span data-stu-id="4f5a8-144">Constant</span></span>  |<span data-ttu-id="4f5a8-145">值</span><span class="sxs-lookup"><span data-stu-id="4f5a8-145">Value</span></span>  |<span data-ttu-id="4f5a8-146">描述</span><span class="sxs-lookup"><span data-stu-id="4f5a8-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="4f5a8-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="4f5a8-147">0x80041003</span></span> | <span data-ttu-id="4f5a8-148">使用者沒有檢視一或多個函式可以傳回的類別權限。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="4f5a8-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4f5a8-149">0x80041001</span></span> | <span data-ttu-id="4f5a8-150">發生意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="4f5a8-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="4f5a8-151">0x80041010</span></span> | <span data-ttu-id="4f5a8-152">`strSuperClass` 不存在。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4f5a8-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4f5a8-153">0x80041008</span></span> | <span data-ttu-id="4f5a8-154">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4f5a8-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4f5a8-155">0x80041006</span></span> | <span data-ttu-id="4f5a8-156">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="4f5a8-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="4f5a8-157">0x80041033</span></span> | <span data-ttu-id="4f5a8-158">WMI 是可能已停止和重新啟動。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="4f5a8-159">呼叫[ConnectServerWmi](connectserverwmi.md)一次。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="4f5a8-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="4f5a8-160">0x80041015</span></span> | <span data-ttu-id="4f5a8-161">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4f5a8-162">0</span><span class="sxs-lookup"><span data-stu-id="4f5a8-162">0</span></span> | <span data-ttu-id="4f5a8-163">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4f5a8-164">備註</span><span class="sxs-lookup"><span data-stu-id="4f5a8-164">Remarks</span></span>

<span data-ttu-id="4f5a8-165">此函式會包裝呼叫[iwbemservices:: Createclassenum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-165">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4f5a8-166">如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f5a8-167">需求</span><span class="sxs-lookup"><span data-stu-id="4f5a8-167">Requirements</span></span>  
 <span data-ttu-id="4f5a8-168">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f5a8-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f5a8-169">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4f5a8-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4f5a8-170">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4f5a8-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5a8-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f5a8-171">See also</span></span>  
[<span data-ttu-id="4f5a8-172">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="4f5a8-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
