---
title: "GetPropertyOrigin 函式 （Unmnaged API 參考）"
description: "GetPropertyOrigin 函式判斷的類別中宣告的屬性。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0a79bfc62ad776cb2bfab2c143d19761d64358bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="3fd59-103">GetPropertyOrigin 函式</span><span class="sxs-lookup"><span data-stu-id="3fd59-103">GetPropertyOrigin function</span></span>
<span data-ttu-id="3fd59-104">決定在宣告屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="3fd59-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="3fd59-105">語法</span><span class="sxs-lookup"><span data-stu-id="3fd59-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="3fd59-106">參數</span><span class="sxs-lookup"><span data-stu-id="3fd59-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3fd59-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="3fd59-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3fd59-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="3fd59-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="3fd59-109">[in]正在要求其主控類別之物件的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3fd59-109">[in] The name of the property for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="3fd59-110">[out]接收類別擁有之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fd59-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="3fd59-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="3fd59-111">Return value</span></span>

<span data-ttu-id="3fd59-112">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="3fd59-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3fd59-113">常數</span><span class="sxs-lookup"><span data-stu-id="3fd59-113">Constant</span></span>  |<span data-ttu-id="3fd59-114">值</span><span class="sxs-lookup"><span data-stu-id="3fd59-114">Value</span></span>  |<span data-ttu-id="3fd59-115">描述</span><span class="sxs-lookup"><span data-stu-id="3fd59-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3fd59-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3fd59-116">0x80041001</span></span> | <span data-ttu-id="3fd59-117">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="3fd59-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="3fd59-118">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="3fd59-118">0x80041002</span></span> | <span data-ttu-id="3fd59-119">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="3fd59-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3fd59-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3fd59-120">0x80041008</span></span> | <span data-ttu-id="3fd59-121">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="3fd59-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3fd59-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3fd59-122">0x80041006</span></span> | <span data-ttu-id="3fd59-123">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="3fd59-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3fd59-124">0</span><span class="sxs-lookup"><span data-stu-id="3fd59-124">0</span></span> | <span data-ttu-id="3fd59-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3fd59-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3fd59-126">備註</span><span class="sxs-lookup"><span data-stu-id="3fd59-126">Remarks</span></span>

<span data-ttu-id="3fd59-127">此函式會包裝呼叫[IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="3fd59-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="3fd59-128">類別可以繼承自一或多個基底類別的屬性，因為開發人員通常會想要判斷指定的方法定義所在的屬性。</span><span class="sxs-lookup"><span data-stu-id="3fd59-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="3fd59-129">`pstrClassName`參數必須是指向有效`BSTR`因為這是在呼叫函式前`out`參數; 此指標會取消配置函式傳回後。</span><span class="sxs-lookup"><span data-stu-id="3fd59-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="3fd59-130">需求</span><span class="sxs-lookup"><span data-stu-id="3fd59-130">Requirements</span></span>  
<span data-ttu-id="3fd59-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3fd59-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd59-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3fd59-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3fd59-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd59-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd59-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fd59-134">See also</span></span>  
[<span data-ttu-id="3fd59-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="3fd59-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
