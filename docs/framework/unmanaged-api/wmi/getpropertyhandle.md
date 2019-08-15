---
title: GetPropertyHandle 函式 (非受控 API 參考)
description: GetPropertyHandle 函數會傳回可識別屬性的唯一控制碼。
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
ms.openlocfilehash: d6dc2792b572aae30e9989c81967b86f340d7b83
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038253"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="72655-103">GetPropertyHandle 函式</span><span class="sxs-lookup"><span data-stu-id="72655-103">GetPropertyHandle function</span></span>

<span data-ttu-id="72655-104">傳回識別屬性的唯一控制代碼。</span><span class="sxs-lookup"><span data-stu-id="72655-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="72655-105">語法</span><span class="sxs-lookup"><span data-stu-id="72655-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="72655-106">參數</span><span class="sxs-lookup"><span data-stu-id="72655-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="72655-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="72655-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="72655-108">在[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="72655-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="72655-109">在以 null 終止的 UTF16 編碼字元字串, 其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="72655-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="72655-110">脫銷[`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration)列舉成員的指標, 表示屬性的 CIM 類型。</span><span class="sxs-lookup"><span data-stu-id="72655-110">[out] A pointer to a [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="72655-111">脫銷包含屬性控制碼之整數的指標。</span><span class="sxs-lookup"><span data-stu-id="72655-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="72655-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="72655-112">Return value</span></span>

<span data-ttu-id="72655-113">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中, 您也可以在程式碼中將它們定義為常數:</span><span class="sxs-lookup"><span data-stu-id="72655-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="72655-114">常數</span><span class="sxs-lookup"><span data-stu-id="72655-114">Constant</span></span>  |<span data-ttu-id="72655-115">值</span><span class="sxs-lookup"><span data-stu-id="72655-115">Value</span></span>  |<span data-ttu-id="72655-116">描述</span><span class="sxs-lookup"><span data-stu-id="72655-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="72655-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="72655-117">0x80041002</span></span> | <span data-ttu-id="72655-118">找不到指定的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="72655-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="72655-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="72655-119">0x80041008</span></span> | <span data-ttu-id="72655-120">參數無效。</span><span class="sxs-lookup"><span data-stu-id="72655-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="72655-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="72655-121">0x8004100c</span></span> | <span data-ttu-id="72655-122">要求的屬性的類型`CIM_OBJECT`為或。 `CIM_ARRAY`</span><span class="sxs-lookup"><span data-stu-id="72655-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="72655-123">0</span><span class="sxs-lookup"><span data-stu-id="72655-123">0</span></span> | <span data-ttu-id="72655-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="72655-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="72655-125">備註</span><span class="sxs-lookup"><span data-stu-id="72655-125">Remarks</span></span>

<span data-ttu-id="72655-126">此函式會包裝對[IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="72655-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="72655-127">使用[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)方法來讀取或寫入屬性值時, 您可以使用此控制碼來識別屬性。</span><span class="sxs-lookup"><span data-stu-id="72655-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="72655-128">可以針對`CIM_OBJECT`和`CIM_ARRAY`以外的所有資料類型的屬性來抓取控制碼。</span><span class="sxs-lookup"><span data-stu-id="72655-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="72655-129">傳回的控制碼可在類別的所有實例之間工作。</span><span class="sxs-lookup"><span data-stu-id="72655-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="72655-130">需求</span><span class="sxs-lookup"><span data-stu-id="72655-130">Requirements</span></span>

<span data-ttu-id="72655-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72655-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="72655-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="72655-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="72655-133">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="72655-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="72655-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72655-134">See also</span></span>

- [<span data-ttu-id="72655-135">WMI 和效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="72655-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
