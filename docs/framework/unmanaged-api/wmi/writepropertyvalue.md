---
title: "WritePropertyValue 函式 （Unmanaged API 參考）"
description: "WritePropertyValue 函式會將位元組寫入屬性。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7221c9e0f1cb49ab0e27130ce69c0527ba903148
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="cebb0-103">WritePropertyValue 函式</span><span class="sxs-lookup"><span data-stu-id="cebb0-103">WritePropertyValue function</span></span>
<span data-ttu-id="cebb0-104">寫入屬性控制代碼所識別的屬性中指定的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="cebb0-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="cebb0-105">語法</span><span class="sxs-lookup"><span data-stu-id="cebb0-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="cebb0-106">參數</span><span class="sxs-lookup"><span data-stu-id="cebb0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cebb0-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="cebb0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cebb0-108">[in]指標[IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="cebb0-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`lHandle`  
<span data-ttu-id="cebb0-109">[in]整數，其中包含識別這個屬性的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="cebb0-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="cebb0-110">控制代碼可以藉由呼叫擷取[GetPropertyHandle](getpropertyhandle.md)函式。</span><span class="sxs-lookup"><span data-stu-id="cebb0-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="cebb0-111">[in]要寫入屬性的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="cebb0-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="cebb0-112">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="cebb0-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="cebb0-113">[out]包含資料的位元組陣列指標。</span><span class="sxs-lookup"><span data-stu-id="cebb0-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="cebb0-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="cebb0-114">Return value</span></span>

<span data-ttu-id="cebb0-115">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="cebb0-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cebb0-116">常數</span><span class="sxs-lookup"><span data-stu-id="cebb0-116">Constant</span></span>  |<span data-ttu-id="cebb0-117">值</span><span class="sxs-lookup"><span data-stu-id="cebb0-117">Value</span></span>  |<span data-ttu-id="cebb0-118">描述</span><span class="sxs-lookup"><span data-stu-id="cebb0-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cebb0-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cebb0-119">0x80041008</span></span> | <span data-ttu-id="cebb0-120">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="cebb0-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="cebb0-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="cebb0-121">0x80041005</span></span> | <span data-ttu-id="cebb0-122">發生類型不符。</span><span class="sxs-lookup"><span data-stu-id="cebb0-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cebb0-123">0</span><span class="sxs-lookup"><span data-stu-id="cebb0-123">0</span></span> | <span data-ttu-id="cebb0-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cebb0-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="cebb0-125">備註</span><span class="sxs-lookup"><span data-stu-id="cebb0-125">Remarks</span></span>

<span data-ttu-id="cebb0-126">此函式會包裝呼叫[IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="cebb0-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="cebb0-127">使用此函式來設定字串和所有其他非`DWORD`或非-`QWORD`資料。</span><span class="sxs-lookup"><span data-stu-id="cebb0-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="cebb0-128">如需非字串屬性值，`lNumBytes`必須是正確的資料大小，指定型別的屬性。</span><span class="sxs-lookup"><span data-stu-id="cebb0-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="cebb0-129">字串屬性值，`lNumBytes`必須是長度以位元組為單位，指定的字串和字串本身，以位元組為單位的平均長度必須是和遵循以 null 結束的字元。</span><span class="sxs-lookup"><span data-stu-id="cebb0-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="cebb0-130">需求</span><span class="sxs-lookup"><span data-stu-id="cebb0-130">Requirements</span></span>  
<span data-ttu-id="cebb0-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cebb0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cebb0-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cebb0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cebb0-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cebb0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebb0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cebb0-134">See also</span></span>  
[<span data-ttu-id="cebb0-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="cebb0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
