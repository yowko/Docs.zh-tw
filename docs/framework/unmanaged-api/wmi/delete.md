---
title: Delete 函式（非受控 API 參考）
description: Delete 函式會從 CIM 類別定義中刪除指定的屬性及其所有限定詞。
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
ms.openlocfilehash: a1bf9bd5d93d1affee649588138456269411d280
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798677"
---
# <a name="delete-function"></a><span data-ttu-id="e24be-103">Delete 函式</span><span class="sxs-lookup"><span data-stu-id="e24be-103">Delete function</span></span>

<span data-ttu-id="e24be-104">從 CIM 類別定義中刪除指定的屬性及其所有限定詞。</span><span class="sxs-lookup"><span data-stu-id="e24be-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e24be-105">語法</span><span class="sxs-lookup"><span data-stu-id="e24be-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="e24be-106">參數</span><span class="sxs-lookup"><span data-stu-id="e24be-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e24be-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="e24be-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e24be-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="e24be-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="e24be-109">在要刪除的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e24be-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="e24be-110">`wszName`必須是有效`LPCWSTR`的指標。</span><span class="sxs-lookup"><span data-stu-id="e24be-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e24be-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e24be-111">Return value</span></span>

<span data-ttu-id="e24be-112">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="e24be-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e24be-113">常數</span><span class="sxs-lookup"><span data-stu-id="e24be-113">Constant</span></span>  |<span data-ttu-id="e24be-114">值</span><span class="sxs-lookup"><span data-stu-id="e24be-114">Value</span></span>  |<span data-ttu-id="e24be-115">描述</span><span class="sxs-lookup"><span data-stu-id="e24be-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="e24be-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e24be-116">0x80041001</span></span> | <span data-ttu-id="e24be-117">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e24be-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="e24be-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="e24be-118">0x80041016</span></span> | <span data-ttu-id="e24be-119">無法刪除屬性。</span><span class="sxs-lookup"><span data-stu-id="e24be-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e24be-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e24be-120">0x80041008</span></span> | <span data-ttu-id="e24be-121">`wszName` 無效。</span><span class="sxs-lookup"><span data-stu-id="e24be-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="e24be-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e24be-122">0x80041002</span></span> | <span data-ttu-id="e24be-123">指定的屬性不存在。</span><span class="sxs-lookup"><span data-stu-id="e24be-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e24be-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e24be-124">0x80041006</span></span> | <span data-ttu-id="e24be-125">記憶體不足，無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="e24be-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="e24be-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="e24be-126">0x8004101c</span></span> | <span data-ttu-id="e24be-127">屬性繼承自基類。</span><span class="sxs-lookup"><span data-stu-id="e24be-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="e24be-128">屬性是系統屬性。</span><span class="sxs-lookup"><span data-stu-id="e24be-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e24be-129">0</span><span class="sxs-lookup"><span data-stu-id="e24be-129">0</span></span> | <span data-ttu-id="e24be-130">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e24be-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="e24be-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="e24be-131">0x80041030</span></span> | <span data-ttu-id="e24be-132">函式已刪除目前類別的覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="e24be-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="e24be-133">父類別中這個屬性的預設值已重新開機。</span><span class="sxs-lookup"><span data-stu-id="e24be-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e24be-134">備註</span><span class="sxs-lookup"><span data-stu-id="e24be-134">Remarks</span></span>

<span data-ttu-id="e24be-135">此函式會包裝對[IWbemClassObject：:D 刪除](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e24be-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e24be-136">需求</span><span class="sxs-lookup"><span data-stu-id="e24be-136">Requirements</span></span>

<span data-ttu-id="e24be-137">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e24be-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e24be-138">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e24be-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e24be-139">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e24be-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e24be-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e24be-140">See also</span></span>

- [<span data-ttu-id="e24be-141">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="e24be-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
