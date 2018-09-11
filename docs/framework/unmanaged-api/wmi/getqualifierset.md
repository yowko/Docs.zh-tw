---
title: GetQualifierSet 函式 （Unmanaged API 參考）
description: GetQualifierSet 函式會擷取為類別或執行個體設定的限定詞。
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 635dc7605af00f2662a9f9553adefafcd25f9452
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267965"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="a3ad1-103">GetQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="a3ad1-103">GetQualifierSet function</span></span>
<span data-ttu-id="a3ad1-104">擷取類別執行個體或類別定義的限定詞集合。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a3ad1-105">語法</span><span class="sxs-lookup"><span data-stu-id="a3ad1-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="a3ad1-106">參數</span><span class="sxs-lookup"><span data-stu-id="a3ad1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a3ad1-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a3ad1-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="a3ad1-109">[out]接收的介面指標，可讓您存取類別物件的限定詞。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="a3ad1-110">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="a3ad1-111">如果發生錯誤，不會傳回新的物件，而且指標將處於未修改。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a3ad1-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="a3ad1-112">Return value</span></span>

<span data-ttu-id="a3ad1-113">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="a3ad1-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a3ad1-114">常數</span><span class="sxs-lookup"><span data-stu-id="a3ad1-114">Constant</span></span>  |<span data-ttu-id="a3ad1-115">值</span><span class="sxs-lookup"><span data-stu-id="a3ad1-115">Value</span></span>  |<span data-ttu-id="a3ad1-116">描述</span><span class="sxs-lookup"><span data-stu-id="a3ad1-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a3ad1-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a3ad1-117">0x80041001</span></span> | <span data-ttu-id="a3ad1-118">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a3ad1-119">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="a3ad1-119">0x80041002</span></span> | <span data-ttu-id="a3ad1-120">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a3ad1-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a3ad1-121">0x80041006</span></span> | <span data-ttu-id="a3ad1-122">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a3ad1-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a3ad1-123">0x80041008</span></span> | <span data-ttu-id="a3ad1-124">參數是`null`。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a3ad1-125">0</span><span class="sxs-lookup"><span data-stu-id="a3ad1-125">0</span></span> | <span data-ttu-id="a3ad1-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a3ad1-127">備註</span><span class="sxs-lookup"><span data-stu-id="a3ad1-127">Remarks</span></span>

<span data-ttu-id="a3ad1-128">此函式會包裝在呼叫[IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset)方法。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span> 

<span data-ttu-id="a3ad1-129">[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)可讓呼叫端新增、 編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="a3ad1-130">這類新增、 編輯或刪除的限定詞適用於整個執行個體或類別定義。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3ad1-131">需求</span><span class="sxs-lookup"><span data-stu-id="a3ad1-131">Requirements</span></span>  
<span data-ttu-id="a3ad1-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3ad1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3ad1-133">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a3ad1-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a3ad1-134">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a3ad1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ad1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3ad1-135">See also</span></span>  
[<span data-ttu-id="a3ad1-136">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="a3ad1-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
