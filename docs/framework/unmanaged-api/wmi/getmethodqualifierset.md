---
title: GetMethodQualifierSet 函式（非受控 API 參考）
description: GetMethodQualifierSet 函數會抓取方法的限定詞集合。
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
ms.openlocfilehash: 86a7788736c3c12cfcfd405de88dfadfb14c1eca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798524"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="a5211-103">GetMethodQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="a5211-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="a5211-104">擷取特定方法的限定詞集合。</span><span class="sxs-lookup"><span data-stu-id="a5211-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a5211-105">語法</span><span class="sxs-lookup"><span data-stu-id="a5211-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="a5211-106">參數</span><span class="sxs-lookup"><span data-stu-id="a5211-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a5211-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="a5211-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a5211-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="a5211-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="a5211-109">在方法名稱。</span><span class="sxs-lookup"><span data-stu-id="a5211-109">[in] The method  name.</span></span> <span data-ttu-id="a5211-110">`wszMethod`必須指向有效`LPCWSTR`的。</span><span class="sxs-lookup"><span data-stu-id="a5211-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="a5211-111">脫銷接收介面指標，允許存取方法的限定詞。</span><span class="sxs-lookup"><span data-stu-id="a5211-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="a5211-112">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="a5211-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="a5211-113">如果發生錯誤，則不會傳回新的物件，並將指標設定為指向`null`。</span><span class="sxs-lookup"><span data-stu-id="a5211-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a5211-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="a5211-114">Return value</span></span>

<span data-ttu-id="a5211-115">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="a5211-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a5211-116">常數</span><span class="sxs-lookup"><span data-stu-id="a5211-116">Constant</span></span>  |<span data-ttu-id="a5211-117">值</span><span class="sxs-lookup"><span data-stu-id="a5211-117">Value</span></span>  |<span data-ttu-id="a5211-118">說明</span><span class="sxs-lookup"><span data-stu-id="a5211-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a5211-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a5211-119">0x80041002</span></span> | <span data-ttu-id="a5211-120">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="a5211-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a5211-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a5211-121">0x80041008</span></span> | <span data-ttu-id="a5211-122">參數為`null`。</span><span class="sxs-lookup"><span data-stu-id="a5211-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a5211-123">0</span><span class="sxs-lookup"><span data-stu-id="a5211-123">0</span></span> | <span data-ttu-id="a5211-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a5211-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a5211-125">備註</span><span class="sxs-lookup"><span data-stu-id="a5211-125">Remarks</span></span>

<span data-ttu-id="a5211-126">此函式會包裝對[IWbemClassObject：： GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a5211-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="a5211-127">只有當目前的物件是 CIM 類別定義時，才支援呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="a5211-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="a5211-128">指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標無法使用方法操作。</span><span class="sxs-lookup"><span data-stu-id="a5211-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="a5211-129">因為每個方法都有自己的限定詞，所以[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)可讓呼叫者加入、編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="a5211-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5211-130">需求</span><span class="sxs-lookup"><span data-stu-id="a5211-130">Requirements</span></span>

<span data-ttu-id="a5211-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5211-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a5211-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a5211-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a5211-133">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a5211-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a5211-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5211-134">See also</span></span>

- [<span data-ttu-id="a5211-135">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="a5211-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
