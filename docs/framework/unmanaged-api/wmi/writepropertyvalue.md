---
title: WritePropertyValue 函式（非受控 API 參考）
description: WritePropertyValue 函數會將位元組寫入至屬性。
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
ms.openlocfilehash: a3c42129835f9b30bed493a0992d49d7e2a458e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798178"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="cc420-103">WritePropertyValue 函式</span><span class="sxs-lookup"><span data-stu-id="cc420-103">WritePropertyValue function</span></span>
<span data-ttu-id="cc420-104">將指定的位元組數目寫入到屬性控制代碼所指定的屬性中。</span><span class="sxs-lookup"><span data-stu-id="cc420-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="cc420-105">語法</span><span class="sxs-lookup"><span data-stu-id="cc420-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="cc420-106">參數</span><span class="sxs-lookup"><span data-stu-id="cc420-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cc420-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="cc420-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cc420-108">在[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="cc420-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="cc420-109">在整數，包含識別這個屬性的控制碼。</span><span class="sxs-lookup"><span data-stu-id="cc420-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="cc420-110">呼叫[GetPropertyHandle](getpropertyhandle.md)函式可以抓取控制碼。</span><span class="sxs-lookup"><span data-stu-id="cc420-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="cc420-111">在要寫入屬性的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="cc420-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="cc420-112">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="cc420-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="cc420-113">脫銷包含資料之位元組陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="cc420-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="cc420-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="cc420-114">Return value</span></span>

<span data-ttu-id="cc420-115">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="cc420-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cc420-116">常數</span><span class="sxs-lookup"><span data-stu-id="cc420-116">Constant</span></span>  |<span data-ttu-id="cc420-117">值</span><span class="sxs-lookup"><span data-stu-id="cc420-117">Value</span></span>  |<span data-ttu-id="cc420-118">描述</span><span class="sxs-lookup"><span data-stu-id="cc420-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cc420-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cc420-119">0x80041008</span></span> | <span data-ttu-id="cc420-120">參數無效。</span><span class="sxs-lookup"><span data-stu-id="cc420-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="cc420-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="cc420-121">0x80041005</span></span> | <span data-ttu-id="cc420-122">發生類型不符。</span><span class="sxs-lookup"><span data-stu-id="cc420-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cc420-123">0</span><span class="sxs-lookup"><span data-stu-id="cc420-123">0</span></span> | <span data-ttu-id="cc420-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cc420-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="cc420-125">備註</span><span class="sxs-lookup"><span data-stu-id="cc420-125">Remarks</span></span>

<span data-ttu-id="cc420-126">此函式會包裝對[IWbemClassObject：： WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="cc420-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="cc420-127">使用此函式可設定字串和所有其他非`DWORD`或`QWORD`非資料。</span><span class="sxs-lookup"><span data-stu-id="cc420-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="cc420-128">針對非字串屬性值， `lNumBytes`必須是指定之屬性類型的正確資料大小。</span><span class="sxs-lookup"><span data-stu-id="cc420-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="cc420-129">對於字串屬性值， `lNumBytes`必須是指定之字串的長度（以位元組為單位），而字串本身必須是長度（以位元組為單位），且後面接著 null 終止字元。</span><span class="sxs-lookup"><span data-stu-id="cc420-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc420-130">需求</span><span class="sxs-lookup"><span data-stu-id="cc420-130">Requirements</span></span>  
<span data-ttu-id="cc420-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc420-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc420-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cc420-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cc420-133">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cc420-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc420-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc420-134">See also</span></span>

- [<span data-ttu-id="cc420-135">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="cc420-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
