---
title: GetPropertyOrigin 函式（非受控 API 參考）
description: GetPropertyOrigin 函式會判斷宣告屬性的類別。
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
ms.openlocfilehash: 0c2d0f23f3dd2d52f73f09c32d4e3118a9ed5ea3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798488"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="ff8df-103">GetPropertyOrigin 函式</span><span class="sxs-lookup"><span data-stu-id="ff8df-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="ff8df-104">判斷屬性在其中宣告的類別。</span><span class="sxs-lookup"><span data-stu-id="ff8df-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ff8df-105">語法</span><span class="sxs-lookup"><span data-stu-id="ff8df-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="ff8df-106">參數</span><span class="sxs-lookup"><span data-stu-id="ff8df-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="ff8df-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="ff8df-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="ff8df-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="ff8df-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="ff8df-109">在正在要求其擁有類別之物件的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ff8df-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="ff8df-110">脫銷接收擁有屬性之類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff8df-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff8df-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ff8df-111">Return value</span></span>

<span data-ttu-id="ff8df-112">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="ff8df-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ff8df-113">常數</span><span class="sxs-lookup"><span data-stu-id="ff8df-113">Constant</span></span>  |<span data-ttu-id="ff8df-114">值</span><span class="sxs-lookup"><span data-stu-id="ff8df-114">Value</span></span>  |<span data-ttu-id="ff8df-115">描述</span><span class="sxs-lookup"><span data-stu-id="ff8df-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="ff8df-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ff8df-116">0x80041001</span></span> | <span data-ttu-id="ff8df-117">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="ff8df-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ff8df-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ff8df-118">0x80041002</span></span> | <span data-ttu-id="ff8df-119">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="ff8df-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ff8df-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ff8df-120">0x80041008</span></span> | <span data-ttu-id="ff8df-121">參數無效。</span><span class="sxs-lookup"><span data-stu-id="ff8df-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ff8df-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ff8df-122">0x80041006</span></span> | <span data-ttu-id="ff8df-123">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="ff8df-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ff8df-124">0</span><span class="sxs-lookup"><span data-stu-id="ff8df-124">0</span></span> | <span data-ttu-id="ff8df-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ff8df-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ff8df-126">備註</span><span class="sxs-lookup"><span data-stu-id="ff8df-126">Remarks</span></span>

<span data-ttu-id="ff8df-127">此函式會包裝對[IWbemClassObject：： GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ff8df-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="ff8df-128">因為類別可以繼承一或多個基類的屬性，所以開發人員通常會想要判斷定義了指定方法的屬性。</span><span class="sxs-lookup"><span data-stu-id="ff8df-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="ff8df-129">在`pstrClassName`呼叫函式`out`之前，參數不得`BSTR`指向有效的，因為這是參數; 此指標不會在函式傳回之後解除配置。</span><span class="sxs-lookup"><span data-stu-id="ff8df-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff8df-130">需求</span><span class="sxs-lookup"><span data-stu-id="ff8df-130">Requirements</span></span>

<span data-ttu-id="ff8df-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff8df-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ff8df-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ff8df-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ff8df-133">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ff8df-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ff8df-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff8df-134">See also</span></span>

- [<span data-ttu-id="ff8df-135">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="ff8df-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
