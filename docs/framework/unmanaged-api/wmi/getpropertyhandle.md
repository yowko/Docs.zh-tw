---
title: GetPropertyHandle 函式 （Unmanaged API 參考）
description: GetPropertyHandle 函式會傳回唯一的控制代碼識別屬性。
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1397188b38066bac6375da0c76e7d66724a75d7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636249"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="495db-103">GetPropertyHandle 函式</span><span class="sxs-lookup"><span data-stu-id="495db-103">GetPropertyHandle function</span></span>

<span data-ttu-id="495db-104">傳回識別屬性的唯一控制代碼。</span><span class="sxs-lookup"><span data-stu-id="495db-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="495db-105">語法</span><span class="sxs-lookup"><span data-stu-id="495db-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="495db-106">參數</span><span class="sxs-lookup"><span data-stu-id="495db-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="495db-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="495db-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="495db-108">[in]指標[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)執行個體。</span><span class="sxs-lookup"><span data-stu-id="495db-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="495db-109">[in]以 null 結尾字串的 UTF16 編碼的字元，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="495db-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="495db-110">[out]指標[ `CIMTYPE` ](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration)列舉的成員，表示屬性的 CIM 型別。</span><span class="sxs-lookup"><span data-stu-id="495db-110">[out] A pointer to a [`CIMTYPE`](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="495db-111">[out]包含屬性控制代碼的整數指標。</span><span class="sxs-lookup"><span data-stu-id="495db-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="495db-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="495db-112">Return value</span></span>

<span data-ttu-id="495db-113">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="495db-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="495db-114">常數</span><span class="sxs-lookup"><span data-stu-id="495db-114">Constant</span></span>  |<span data-ttu-id="495db-115">值</span><span class="sxs-lookup"><span data-stu-id="495db-115">Value</span></span>  |<span data-ttu-id="495db-116">描述</span><span class="sxs-lookup"><span data-stu-id="495db-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="495db-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="495db-117">0x80041002</span></span> | <span data-ttu-id="495db-118">找不到指定的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="495db-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="495db-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="495db-119">0x80041008</span></span> | <span data-ttu-id="495db-120">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="495db-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="495db-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="495db-121">0x8004100c</span></span> | <span data-ttu-id="495db-122">要求的屬性屬於型別是`CIM_OBJECT`或`CIM_ARRAY`。</span><span class="sxs-lookup"><span data-stu-id="495db-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="495db-123">0</span><span class="sxs-lookup"><span data-stu-id="495db-123">0</span></span> | <span data-ttu-id="495db-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="495db-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="495db-125">備註</span><span class="sxs-lookup"><span data-stu-id="495db-125">Remarks</span></span>

<span data-ttu-id="495db-126">此函式會包裝在呼叫[IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle)方法。</span><span class="sxs-lookup"><span data-stu-id="495db-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="495db-127">您可以使用此控制代碼識別屬性使用時[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)方法來讀取或寫入屬性值。</span><span class="sxs-lookup"><span data-stu-id="495db-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="495db-128">控制代碼可以擷取所有資料類型的屬性以外`CIM_OBJECT`和`CIM_ARRAY`。</span><span class="sxs-lookup"><span data-stu-id="495db-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="495db-129">傳回類別所有執行個體之間的控制代碼的工作。</span><span class="sxs-lookup"><span data-stu-id="495db-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="495db-130">需求</span><span class="sxs-lookup"><span data-stu-id="495db-130">Requirements</span></span>

<span data-ttu-id="495db-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="495db-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="495db-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="495db-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="495db-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="495db-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="495db-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="495db-134">See also</span></span>

- [<span data-ttu-id="495db-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="495db-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
