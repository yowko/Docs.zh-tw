---
title: WritePropertyValue function (Unmanaged API Reference)
description: The WritePropertyValue function writes bytes to a property.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107295"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="b62ba-103">WritePropertyValue function</span><span class="sxs-lookup"><span data-stu-id="b62ba-103">WritePropertyValue function</span></span>
<span data-ttu-id="b62ba-104">將指定的位元組數目寫入到屬性控制代碼所指定的屬性中。</span><span class="sxs-lookup"><span data-stu-id="b62ba-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b62ba-105">語法</span><span class="sxs-lookup"><span data-stu-id="b62ba-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="b62ba-106">參數</span><span class="sxs-lookup"><span data-stu-id="b62ba-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b62ba-107">[in] This parameter is unused.</span><span class="sxs-lookup"><span data-stu-id="b62ba-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b62ba-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span><span class="sxs-lookup"><span data-stu-id="b62ba-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="b62ba-109">[in] An integer that contains the handle that identifies this property.</span><span class="sxs-lookup"><span data-stu-id="b62ba-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="b62ba-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span><span class="sxs-lookup"><span data-stu-id="b62ba-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="b62ba-111">[in] The number of bytes being written to the property.</span><span class="sxs-lookup"><span data-stu-id="b62ba-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="b62ba-112">See the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="b62ba-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="b62ba-113">[out] A pointer to the byte array that contains the data.</span><span class="sxs-lookup"><span data-stu-id="b62ba-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="b62ba-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="b62ba-114">Return value</span></span>

<span data-ttu-id="b62ba-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span><span class="sxs-lookup"><span data-stu-id="b62ba-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b62ba-116">常數</span><span class="sxs-lookup"><span data-stu-id="b62ba-116">Constant</span></span>  |<span data-ttu-id="b62ba-117">值</span><span class="sxs-lookup"><span data-stu-id="b62ba-117">Value</span></span>  |<span data-ttu-id="b62ba-118">描述</span><span class="sxs-lookup"><span data-stu-id="b62ba-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b62ba-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b62ba-119">0x80041008</span></span> | <span data-ttu-id="b62ba-120">A parameter is not valid.</span><span class="sxs-lookup"><span data-stu-id="b62ba-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="b62ba-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="b62ba-121">0x80041005</span></span> | <span data-ttu-id="b62ba-122">A type mismatch occurred.</span><span class="sxs-lookup"><span data-stu-id="b62ba-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b62ba-123">0</span><span class="sxs-lookup"><span data-stu-id="b62ba-123">0</span></span> | <span data-ttu-id="b62ba-124">The function call was successful.</span><span class="sxs-lookup"><span data-stu-id="b62ba-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b62ba-125">備註</span><span class="sxs-lookup"><span data-stu-id="b62ba-125">Remarks</span></span>

<span data-ttu-id="b62ba-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span><span class="sxs-lookup"><span data-stu-id="b62ba-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="b62ba-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span><span class="sxs-lookup"><span data-stu-id="b62ba-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="b62ba-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span><span class="sxs-lookup"><span data-stu-id="b62ba-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="b62ba-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span><span class="sxs-lookup"><span data-stu-id="b62ba-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="b62ba-130">需求</span><span class="sxs-lookup"><span data-stu-id="b62ba-130">Requirements</span></span>  
<span data-ttu-id="b62ba-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b62ba-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b62ba-132">**Header:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b62ba-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b62ba-133">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b62ba-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62ba-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="b62ba-134">See also</span></span>

- [<span data-ttu-id="b62ba-135">WMI and Performance Counters (Unmanaged API Reference)</span><span class="sxs-lookup"><span data-stu-id="b62ba-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
