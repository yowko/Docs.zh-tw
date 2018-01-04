---
title: "GetMethodQualifierSet 函式 （Unmanaged API 參考）"
description: "GetMethodQualifierSet 函式會擷取該方法的辨識符號組。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2999bef31576cf2bc025868260c2b1782a9b69f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="4c08d-103">GetMethodQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="4c08d-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="4c08d-104">擷取特定的方法設定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="4c08d-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4c08d-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c08d-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="4c08d-106">參數</span><span class="sxs-lookup"><span data-stu-id="4c08d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4c08d-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="4c08d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4c08d-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="4c08d-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="4c08d-109">[in]方法名稱。</span><span class="sxs-lookup"><span data-stu-id="4c08d-109">[in] The method  name.</span></span> <span data-ttu-id="4c08d-110">`wszMethod`必須指向有效`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="4c08d-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="4c08d-111">[out]接收介面指標，可讓您存取方法的限定詞。</span><span class="sxs-lookup"><span data-stu-id="4c08d-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="4c08d-112">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="4c08d-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="4c08d-113">如果發生錯誤、 沒有傳回新的物件，並將指標設定為指向`null`。</span><span class="sxs-lookup"><span data-stu-id="4c08d-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4c08d-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="4c08d-114">Return value</span></span>

<span data-ttu-id="4c08d-115">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="4c08d-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4c08d-116">常數</span><span class="sxs-lookup"><span data-stu-id="4c08d-116">Constant</span></span>  |<span data-ttu-id="4c08d-117">值</span><span class="sxs-lookup"><span data-stu-id="4c08d-117">Value</span></span>  |<span data-ttu-id="4c08d-118">描述</span><span class="sxs-lookup"><span data-stu-id="4c08d-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4c08d-119">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="4c08d-119">0x80041002</span></span> | <span data-ttu-id="4c08d-120">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="4c08d-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4c08d-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4c08d-121">0x80041008</span></span> | <span data-ttu-id="4c08d-122">參數是`null`。</span><span class="sxs-lookup"><span data-stu-id="4c08d-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4c08d-123">0</span><span class="sxs-lookup"><span data-stu-id="4c08d-123">0</span></span> | <span data-ttu-id="4c08d-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4c08d-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4c08d-125">備註</span><span class="sxs-lookup"><span data-stu-id="4c08d-125">Remarks</span></span>

<span data-ttu-id="4c08d-126">此函式會包裝呼叫[IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="4c08d-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="4c08d-127">呼叫此函式僅支援目前的物件是 CIM 類別定義。</span><span class="sxs-lookup"><span data-stu-id="4c08d-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="4c08d-128">操作方法不適用於[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters 指向 CIM 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4c08d-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="4c08d-129">因為每個方法可能會有它自己的限定詞， [IWbemQualifierSet 指標](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)可讓呼叫者新增、 編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="4c08d-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c08d-130">需求</span><span class="sxs-lookup"><span data-stu-id="4c08d-130">Requirements</span></span>  
<span data-ttu-id="4c08d-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c08d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c08d-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4c08d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4c08d-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c08d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c08d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c08d-134">See also</span></span>  
[<span data-ttu-id="4c08d-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="4c08d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
