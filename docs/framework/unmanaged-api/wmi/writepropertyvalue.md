---
title: WritePropertyValue 函式 （Unmanaged API 參考）
description: WritePropertyValue 函式會將位元組寫入屬性。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a98103367f497b18f9b8fbd61a37abf9816b8356
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107935"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="62652-103">WritePropertyValue 函式</span><span class="sxs-lookup"><span data-stu-id="62652-103">WritePropertyValue function</span></span>
<span data-ttu-id="62652-104">將指定的位元組數目寫入到屬性控制代碼所指定的屬性中。</span><span class="sxs-lookup"><span data-stu-id="62652-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="62652-105">語法</span><span class="sxs-lookup"><span data-stu-id="62652-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="62652-106">參數</span><span class="sxs-lookup"><span data-stu-id="62652-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="62652-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="62652-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="62652-108">[in]指標[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)執行個體。</span><span class="sxs-lookup"><span data-stu-id="62652-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="62652-109">[in]整數，包含識別這個屬性的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="62652-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="62652-110">控制代碼可以擷取由呼叫[GetPropertyHandle](getpropertyhandle.md)函式。</span><span class="sxs-lookup"><span data-stu-id="62652-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="62652-111">[in]寫入屬性的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="62652-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="62652-112">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="62652-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="62652-113">[out]包含資料的位元組陣列指標。</span><span class="sxs-lookup"><span data-stu-id="62652-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="62652-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="62652-114">Return value</span></span>

<span data-ttu-id="62652-115">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="62652-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="62652-116">常數</span><span class="sxs-lookup"><span data-stu-id="62652-116">Constant</span></span>  |<span data-ttu-id="62652-117">值</span><span class="sxs-lookup"><span data-stu-id="62652-117">Value</span></span>  |<span data-ttu-id="62652-118">描述</span><span class="sxs-lookup"><span data-stu-id="62652-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="62652-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="62652-119">0x80041008</span></span> | <span data-ttu-id="62652-120">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="62652-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="62652-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="62652-121">0x80041005</span></span> | <span data-ttu-id="62652-122">發生類型不符。</span><span class="sxs-lookup"><span data-stu-id="62652-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="62652-123">0</span><span class="sxs-lookup"><span data-stu-id="62652-123">0</span></span> | <span data-ttu-id="62652-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="62652-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="62652-125">備註</span><span class="sxs-lookup"><span data-stu-id="62652-125">Remarks</span></span>

<span data-ttu-id="62652-126">此函式會包裝在呼叫[IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)方法。</span><span class="sxs-lookup"><span data-stu-id="62652-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="62652-127">使用此函式來設定字串和所有其他非`DWORD`或非-`QWORD`資料。</span><span class="sxs-lookup"><span data-stu-id="62652-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="62652-128">對於非字串屬性值，`lNumBytes`必須是正確的資料大小，指定型別的屬性。</span><span class="sxs-lookup"><span data-stu-id="62652-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="62652-129">如需字串屬性值，`lNumBytes`必須是長度以位元組為單位，指定的字串和字串本身必須以位元組為單位，甚至是長度，而且後面接著 null 結束字元。</span><span class="sxs-lookup"><span data-stu-id="62652-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="62652-130">需求</span><span class="sxs-lookup"><span data-stu-id="62652-130">Requirements</span></span>  
<span data-ttu-id="62652-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62652-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62652-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="62652-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="62652-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62652-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62652-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62652-134">See also</span></span>

- [<span data-ttu-id="62652-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="62652-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
