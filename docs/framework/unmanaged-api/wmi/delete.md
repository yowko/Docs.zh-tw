---
title: 刪除函式 （Unmanaged API 參考）
description: 刪除函式會從 CIM 類別定義中刪除指定的屬性和所有其限定詞。
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1a26db7785a8a378fa541308ecc6aee30fa87ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049280"
---
# <a name="delete-function"></a><span data-ttu-id="4450a-103">Delete 函式</span><span class="sxs-lookup"><span data-stu-id="4450a-103">Delete function</span></span>

<span data-ttu-id="4450a-104">刪除指定的屬性和其限定詞的所有從 CIM 類別定義。</span><span class="sxs-lookup"><span data-stu-id="4450a-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="4450a-105">語法</span><span class="sxs-lookup"><span data-stu-id="4450a-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="4450a-106">參數</span><span class="sxs-lookup"><span data-stu-id="4450a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="4450a-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="4450a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="4450a-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="4450a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="4450a-109">[in]要刪除之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4450a-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="4450a-110">`wszName` 必須是有效的指標`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="4450a-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="4450a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4450a-111">Return value</span></span>

<span data-ttu-id="4450a-112">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="4450a-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4450a-113">常數</span><span class="sxs-lookup"><span data-stu-id="4450a-113">Constant</span></span>  |<span data-ttu-id="4450a-114">值</span><span class="sxs-lookup"><span data-stu-id="4450a-114">Value</span></span>  |<span data-ttu-id="4450a-115">描述</span><span class="sxs-lookup"><span data-stu-id="4450a-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="4450a-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4450a-116">0x80041001</span></span> | <span data-ttu-id="4450a-117">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4450a-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="4450a-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="4450a-118">0x80041016</span></span> | <span data-ttu-id="4450a-119">無法刪除屬性。</span><span class="sxs-lookup"><span data-stu-id="4450a-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4450a-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4450a-120">0x80041008</span></span> | <span data-ttu-id="4450a-121">`wszName` 無效。</span><span class="sxs-lookup"><span data-stu-id="4450a-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="4450a-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4450a-122">0x80041002</span></span> | <span data-ttu-id="4450a-123">指定的屬性不存在。</span><span class="sxs-lookup"><span data-stu-id="4450a-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4450a-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4450a-124">0x80041006</span></span> | <span data-ttu-id="4450a-125">沒有足夠的記憶體來完成此作業。</span><span class="sxs-lookup"><span data-stu-id="4450a-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="4450a-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="4450a-126">0x8004101c</span></span> | <span data-ttu-id="4450a-127">屬性被繼承自基底類別。</span><span class="sxs-lookup"><span data-stu-id="4450a-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="4450a-128">系統屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="4450a-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4450a-129">0</span><span class="sxs-lookup"><span data-stu-id="4450a-129">0</span></span> | <span data-ttu-id="4450a-130">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4450a-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="4450a-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="4450a-131">0x80041030</span></span> | <span data-ttu-id="4450a-132">函式會刪除目前的類別覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="4450a-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="4450a-133">已重新啟動此父類別中屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="4450a-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4450a-134">備註</span><span class="sxs-lookup"><span data-stu-id="4450a-134">Remarks</span></span>

<span data-ttu-id="4450a-135">此函式會包裝在呼叫[IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete)方法。</span><span class="sxs-lookup"><span data-stu-id="4450a-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4450a-136">需求</span><span class="sxs-lookup"><span data-stu-id="4450a-136">Requirements</span></span>

<span data-ttu-id="4450a-137">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4450a-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="4450a-138">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4450a-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="4450a-139">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4450a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4450a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4450a-140">See also</span></span>

- [<span data-ttu-id="4450a-141">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="4450a-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)