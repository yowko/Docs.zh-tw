---
title: "CloneEnumWbemClassObject 函式 （Unmanaged API 參考）"
description: "CloneEnumWbemClassObject 函式可讓列舉值的邏輯副本。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CloneEnumWbemClassObject
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CloneEnumWbemClassObject
helpviewer_keywords: CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a4103a0103a334a0e5eace32d8fcf1b365917b8
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="5bcd0-103">CloneEnumWbemClassObject 函式</span><span class="sxs-lookup"><span data-stu-id="5bcd0-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="5bcd0-104">讓列舉值，並保留其目前位置列舉中的邏輯副本。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5bcd0-105">語法</span><span class="sxs-lookup"><span data-stu-id="5bcd0-105">Syntax</span></span>  
  
```  
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```  

## <a name="parameters"></a><span data-ttu-id="5bcd0-106">參數</span><span class="sxs-lookup"><span data-stu-id="5bcd0-106">Parameters</span></span>

`ppEnum`  
<span data-ttu-id="5bcd0-107">[out]接收新的指標[IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-107">[out] Receives a pointer to a new [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx).</span></span>

`authLevel`  
<span data-ttu-id="5bcd0-108">[in]授權層級。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-108">[in] The authorization level.</span></span>

<span data-ttu-id="5bcd0-109">`impLevel`[in]模擬等級。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-109">`impLevel` [in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`  
<span data-ttu-id="5bcd0-110">[out]指標[IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx)可以被複製的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-110">[out] A pointer to the [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) instance to be cloned.</span></span>

`strUser`   
<span data-ttu-id="5bcd0-111">[in]使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-111">[in] The user name.</span></span> <span data-ttu-id="5bcd0-112">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="5bcd0-113">[in]密碼。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-113">[in] The password.</span></span> <span data-ttu-id="5bcd0-114">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="5bcd0-115">[in]使用者的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-115">[in] The domain name of the user.</span></span> <span data-ttu-id="5bcd0-116">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="5bcd0-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="5bcd0-117">Return value</span></span>

<span data-ttu-id="5bcd0-118">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="5bcd0-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5bcd0-119">常數</span><span class="sxs-lookup"><span data-stu-id="5bcd0-119">Constant</span></span>  |<span data-ttu-id="5bcd0-120">值</span><span class="sxs-lookup"><span data-stu-id="5bcd0-120">Value</span></span>  |<span data-ttu-id="5bcd0-121">說明</span><span class="sxs-lookup"><span data-stu-id="5bcd0-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5bcd0-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5bcd0-122">0x80041001</span></span> | <span data-ttu-id="5bcd0-123">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5bcd0-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5bcd0-124">0x80041008</span></span> | <span data-ttu-id="5bcd0-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5bcd0-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5bcd0-126">0x80041006</span></span> | <span data-ttu-id="5bcd0-127">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="5bcd0-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="5bcd0-128">0x80041015</span></span> | <span data-ttu-id="5bcd0-129">目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5bcd0-130">0</span><span class="sxs-lookup"><span data-stu-id="5bcd0-130">0</span></span> | <span data-ttu-id="5bcd0-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5bcd0-132">備註</span><span class="sxs-lookup"><span data-stu-id="5bcd0-132">Remarks</span></span>

<span data-ttu-id="5bcd0-133">此函式會包裝呼叫[IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-133">This function wraps a call to the [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5bcd0-134">這個方法建立僅 「 盡力 」 複本。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="5bcd0-135">由於許多 CIM 物件的動態本質，可能是新的列舉值無法列舉來源列舉值相同的物件集合。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>  

<span data-ttu-id="5bcd0-136">如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="5bcd0-137">範例</span><span class="sxs-lookup"><span data-stu-id="5bcd0-137">Example</span></span>

<span data-ttu-id="5bcd0-138">如需範例，請參閱[IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-138">For an example, see the [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5bcd0-139">需求</span><span class="sxs-lookup"><span data-stu-id="5bcd0-139">Requirements</span></span>  
 <span data-ttu-id="5bcd0-140">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bcd0-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bcd0-141">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5bcd0-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5bcd0-142">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5bcd0-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bcd0-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="5bcd0-143">See also</span></span>  
[<span data-ttu-id="5bcd0-144">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="5bcd0-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
