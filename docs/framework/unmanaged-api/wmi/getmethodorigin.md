---
title: GetMethodOrigin 函式 （Unmanaged API 參考）
description: GetMethodOrigin 函式會判斷在宣告方法的類別。
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1cc754fcf7d1defa815bb0a74b7c2b4a6909478
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877894"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="b6536-103">GetMethodOrigin 函式</span><span class="sxs-lookup"><span data-stu-id="b6536-103">GetMethodOrigin function</span></span>
<span data-ttu-id="b6536-104">判斷方法在其中宣告的類別。</span><span class="sxs-lookup"><span data-stu-id="b6536-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b6536-105">語法</span><span class="sxs-lookup"><span data-stu-id="b6536-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="b6536-106">參數</span><span class="sxs-lookup"><span data-stu-id="b6536-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b6536-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="b6536-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b6536-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6536-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="b6536-109">[in]正在要求其擁有的類別之物件的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="b6536-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="b6536-110">[out]接收類別擁有之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6536-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="b6536-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6536-111">Return value</span></span>

<span data-ttu-id="b6536-112">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="b6536-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b6536-113">常數</span><span class="sxs-lookup"><span data-stu-id="b6536-113">Constant</span></span>  |<span data-ttu-id="b6536-114">值</span><span class="sxs-lookup"><span data-stu-id="b6536-114">Value</span></span>  |<span data-ttu-id="b6536-115">描述</span><span class="sxs-lookup"><span data-stu-id="b6536-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="b6536-116">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="b6536-116">0x80041002</span></span> | <span data-ttu-id="b6536-117">找不到指定的方法。</span><span class="sxs-lookup"><span data-stu-id="b6536-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b6536-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b6536-118">0x80041008</span></span> | <span data-ttu-id="b6536-119">找不到有效的一或多個參數。</span><span class="sxs-lookup"><span data-stu-id="b6536-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b6536-120">0</span><span class="sxs-lookup"><span data-stu-id="b6536-120">0</span></span> | <span data-ttu-id="b6536-121">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b6536-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b6536-122">備註</span><span class="sxs-lookup"><span data-stu-id="b6536-122">Remarks</span></span>

<span data-ttu-id="b6536-123">此函式會包裝在呼叫[IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法。</span><span class="sxs-lookup"><span data-stu-id="b6536-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="b6536-124">因為類別可以繼承自一或多個基底類別的方法，開發人員通常會想要判斷指定的方法定義所在的類別。</span><span class="sxs-lookup"><span data-stu-id="b6536-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="b6536-125">`pstrClassName`參數必須不指向有效`BSTR`呼叫此函式，因為這是之前`out`參數，此指標未解除配置函式傳回後，此。</span><span class="sxs-lookup"><span data-stu-id="b6536-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6536-126">需求</span><span class="sxs-lookup"><span data-stu-id="b6536-126">Requirements</span></span>  
<span data-ttu-id="b6536-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6536-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6536-128">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b6536-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b6536-129">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b6536-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6536-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6536-130">See also</span></span>  
[<span data-ttu-id="b6536-131">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="b6536-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
