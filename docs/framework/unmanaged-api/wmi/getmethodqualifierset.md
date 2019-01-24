---
title: GetMethodQualifierSet 函式 （Unmanaged API 參考）
description: GetMethodQualifierSet 函式會擷取方法的限定詞集。
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f197851d4d7d470c6c34e4f5607e1791e724770
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681621"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="eb4de-103">GetMethodQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="eb4de-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="eb4de-104">擷取特定方法的限定詞集合。</span><span class="sxs-lookup"><span data-stu-id="eb4de-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="eb4de-105">語法</span><span class="sxs-lookup"><span data-stu-id="eb4de-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="eb4de-106">參數</span><span class="sxs-lookup"><span data-stu-id="eb4de-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="eb4de-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="eb4de-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="eb4de-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb4de-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`  
<span data-ttu-id="eb4de-109">[in]方法名稱。</span><span class="sxs-lookup"><span data-stu-id="eb4de-109">[in] The method  name.</span></span> <span data-ttu-id="eb4de-110">`wszMethod` 必須指向有效`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="eb4de-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="eb4de-111">[out]接收的介面指標，可讓您存取方法的限定詞。</span><span class="sxs-lookup"><span data-stu-id="eb4de-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="eb4de-112">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="eb4de-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="eb4de-113">如果錯誤時，不會傳回新的物件，而指標會設定為指向`null`。</span><span class="sxs-lookup"><span data-stu-id="eb4de-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="eb4de-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="eb4de-114">Return value</span></span>

<span data-ttu-id="eb4de-115">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="eb4de-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="eb4de-116">常數</span><span class="sxs-lookup"><span data-stu-id="eb4de-116">Constant</span></span>  |<span data-ttu-id="eb4de-117">值</span><span class="sxs-lookup"><span data-stu-id="eb4de-117">Value</span></span>  |<span data-ttu-id="eb4de-118">描述</span><span class="sxs-lookup"><span data-stu-id="eb4de-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="eb4de-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="eb4de-119">0x80041002</span></span> | <span data-ttu-id="eb4de-120">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="eb4de-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="eb4de-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="eb4de-121">0x80041008</span></span> | <span data-ttu-id="eb4de-122">參數是`null`。</span><span class="sxs-lookup"><span data-stu-id="eb4de-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="eb4de-123">0</span><span class="sxs-lookup"><span data-stu-id="eb4de-123">0</span></span> | <span data-ttu-id="eb4de-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="eb4de-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="eb4de-125">備註</span><span class="sxs-lookup"><span data-stu-id="eb4de-125">Remarks</span></span>

<span data-ttu-id="eb4de-126">此函式會包裝在呼叫[IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset)方法。</span><span class="sxs-lookup"><span data-stu-id="eb4de-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span> 

<span data-ttu-id="eb4de-127">只有當目前的物件是 CIM 類別定義時，才支援此函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="eb4de-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="eb4de-128">方法操作不適用於[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters 指向 CIM 執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb4de-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters that point to CIM instances.</span></span>

<span data-ttu-id="eb4de-129">因為每一種方法可能有它自己的限定詞[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)可讓呼叫端新增、 編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="eb4de-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb4de-130">需求</span><span class="sxs-lookup"><span data-stu-id="eb4de-130">Requirements</span></span>  
<span data-ttu-id="eb4de-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb4de-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb4de-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="eb4de-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="eb4de-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eb4de-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4de-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb4de-134">See also</span></span>
- [<span data-ttu-id="eb4de-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="eb4de-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
