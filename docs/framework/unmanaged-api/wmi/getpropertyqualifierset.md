---
title: GetPropertyQualifierSet 函式 （Unmanaged API 參考）
description: GetPropertyQualifierSet 函式會擷取為屬性設定的限定詞。
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcddca2e435a3f5bf4b8d083784613254d9801a4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259765"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="945dd-103">GetPropertyQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="945dd-103">GetPropertyQualifierSet function</span></span>
<span data-ttu-id="945dd-104">擷取特定屬性的限定詞集合。</span><span class="sxs-lookup"><span data-stu-id="945dd-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="945dd-105">語法</span><span class="sxs-lookup"><span data-stu-id="945dd-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="945dd-106">參數</span><span class="sxs-lookup"><span data-stu-id="945dd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="945dd-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="945dd-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="945dd-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="945dd-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`  
<span data-ttu-id="945dd-109">[in]屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="945dd-109">[in] The property  name.</span></span> <span data-ttu-id="945dd-110">`wszProperty` 必須指向有效`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="945dd-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="945dd-111">[out]接收的介面指標，可讓您存取屬性的限定詞。</span><span class="sxs-lookup"><span data-stu-id="945dd-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="945dd-112">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="945dd-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="945dd-113">如果錯誤時，不會傳回新的物件，而指標會設定為指向`null`。</span><span class="sxs-lookup"><span data-stu-id="945dd-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="945dd-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="945dd-114">Return value</span></span>

<span data-ttu-id="945dd-115">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="945dd-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="945dd-116">常數</span><span class="sxs-lookup"><span data-stu-id="945dd-116">Constant</span></span>  |<span data-ttu-id="945dd-117">值</span><span class="sxs-lookup"><span data-stu-id="945dd-117">Value</span></span>  |<span data-ttu-id="945dd-118">描述</span><span class="sxs-lookup"><span data-stu-id="945dd-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="945dd-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="945dd-119">0x80041001</span></span> | <span data-ttu-id="945dd-120">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="945dd-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="945dd-121">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="945dd-121">0x80041002</span></span> | <span data-ttu-id="945dd-122">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="945dd-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="945dd-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="945dd-123">0x80041006</span></span> | <span data-ttu-id="945dd-124">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="945dd-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="945dd-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="945dd-125">0x80041008</span></span> | <span data-ttu-id="945dd-126">參數是`null`。</span><span class="sxs-lookup"><span data-stu-id="945dd-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="945dd-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="945dd-127">0x80041030</span></span> | <span data-ttu-id="945dd-128">函式會嘗試取得系統屬性的限定詞。</span><span class="sxs-lookup"><span data-stu-id="945dd-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="945dd-129">0</span><span class="sxs-lookup"><span data-stu-id="945dd-129">0</span></span> | <span data-ttu-id="945dd-130">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="945dd-130">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="945dd-131">備註</span><span class="sxs-lookup"><span data-stu-id="945dd-131">Remarks</span></span>

<span data-ttu-id="945dd-132">此函式會包裝在呼叫[IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset)方法。</span><span class="sxs-lookup"><span data-stu-id="945dd-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span> 

<span data-ttu-id="945dd-133">只有當目前的物件是 CIM 類別定義時，才支援此函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="945dd-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="945dd-134">方法操作不適用於[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters 指向 CIM 執行個體。</span><span class="sxs-lookup"><span data-stu-id="945dd-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters that point to CIM instances.</span></span>

<span data-ttu-id="945dd-135">因為每一種方法可能有它自己的限定詞[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)可讓呼叫端新增、 編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="945dd-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="945dd-136">由於系統內容不有任何限定詞，則函數會傳回`WBEM_E_SYSTEM_PROPERTY`如果您嘗試取得[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標是否為系統屬性。</span><span class="sxs-lookup"><span data-stu-id="945dd-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="945dd-137">需求</span><span class="sxs-lookup"><span data-stu-id="945dd-137">Requirements</span></span>  
<span data-ttu-id="945dd-138">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="945dd-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="945dd-139">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="945dd-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="945dd-140">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="945dd-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945dd-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="945dd-141">See also</span></span>  
[<span data-ttu-id="945dd-142">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="945dd-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
