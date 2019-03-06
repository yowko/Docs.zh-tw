---
title: GetPropertyOrigin 函式 （Unmanaged API 參考）
description: GetPropertyOrigin 函式會判斷在宣告屬性的類別。
ms.date: 11/06/2017
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
ms.openlocfilehash: 42e5cd6ee438b33fd07fd7c3242cc3c2a6513dd9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368869"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="ee916-103">GetPropertyOrigin 函式</span><span class="sxs-lookup"><span data-stu-id="ee916-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="ee916-104">判斷屬性在其中宣告的類別。</span><span class="sxs-lookup"><span data-stu-id="ee916-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ee916-105">語法</span><span class="sxs-lookup"><span data-stu-id="ee916-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="ee916-106">參數</span><span class="sxs-lookup"><span data-stu-id="ee916-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="ee916-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="ee916-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="ee916-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee916-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="ee916-109">[in]正在要求其擁有的類別之物件的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ee916-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="ee916-110">[out]接收類別擁有之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee916-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="ee916-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ee916-111">Return value</span></span>

<span data-ttu-id="ee916-112">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="ee916-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ee916-113">常數</span><span class="sxs-lookup"><span data-stu-id="ee916-113">Constant</span></span>  |<span data-ttu-id="ee916-114">值</span><span class="sxs-lookup"><span data-stu-id="ee916-114">Value</span></span>  |<span data-ttu-id="ee916-115">描述</span><span class="sxs-lookup"><span data-stu-id="ee916-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="ee916-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ee916-116">0x80041001</span></span> | <span data-ttu-id="ee916-117">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="ee916-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ee916-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ee916-118">0x80041002</span></span> | <span data-ttu-id="ee916-119">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="ee916-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ee916-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ee916-120">0x80041008</span></span> | <span data-ttu-id="ee916-121">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="ee916-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ee916-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ee916-122">0x80041006</span></span> | <span data-ttu-id="ee916-123">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="ee916-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ee916-124">0</span><span class="sxs-lookup"><span data-stu-id="ee916-124">0</span></span> | <span data-ttu-id="ee916-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ee916-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ee916-126">備註</span><span class="sxs-lookup"><span data-stu-id="ee916-126">Remarks</span></span>

<span data-ttu-id="ee916-127">此函式會包裝在呼叫[IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin)方法。</span><span class="sxs-lookup"><span data-stu-id="ee916-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="ee916-128">因為類別可以繼承屬性，從一或多個基底類別，開發人員通常會想要判斷指定的方法定義所在的屬性。</span><span class="sxs-lookup"><span data-stu-id="ee916-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="ee916-129">`pstrClassName`參數必須不指向有效`BSTR`呼叫此函式，因為這是之前`out`參數，此指標未解除配置函式傳回後，此。</span><span class="sxs-lookup"><span data-stu-id="ee916-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee916-130">需求</span><span class="sxs-lookup"><span data-stu-id="ee916-130">Requirements</span></span>

<span data-ttu-id="ee916-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee916-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ee916-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ee916-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ee916-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee916-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ee916-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee916-134">See also</span></span>

- [<span data-ttu-id="ee916-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="ee916-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)