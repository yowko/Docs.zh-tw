---
title: 'WritePropertyValue 函式 (非受控 API 參考) '
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
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729404"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="807a4-103">WritePropertyValue 函式</span><span class="sxs-lookup"><span data-stu-id="807a4-103">WritePropertyValue function</span></span>

<span data-ttu-id="807a4-104">將指定的位元組數目寫入到屬性控制代碼所指定的屬性中。</span><span class="sxs-lookup"><span data-stu-id="807a4-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="807a4-105">語法</span><span class="sxs-lookup"><span data-stu-id="807a4-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="807a4-106">參數</span><span class="sxs-lookup"><span data-stu-id="807a4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="807a4-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="807a4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="807a4-108">在 [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="807a4-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="807a4-109">在包含識別這個屬性之控制碼的整數。</span><span class="sxs-lookup"><span data-stu-id="807a4-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="807a4-110">您可以藉由呼叫 [GetPropertyHandle](getpropertyhandle.md) 函數來抓取控制碼。</span><span class="sxs-lookup"><span data-stu-id="807a4-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="807a4-111">在要寫入屬性的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="807a4-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="807a4-112">如需詳細資訊，請參閱「 [備註](#remarks) 」一節。</span><span class="sxs-lookup"><span data-stu-id="807a4-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="807a4-113">`pHandle` 擴展包含資料之位元組陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="807a4-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="807a4-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="807a4-114">Return value</span></span>

<span data-ttu-id="807a4-115">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="807a4-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="807a4-116">常數</span><span class="sxs-lookup"><span data-stu-id="807a4-116">Constant</span></span>  |<span data-ttu-id="807a4-117">值</span><span class="sxs-lookup"><span data-stu-id="807a4-117">Value</span></span>  |<span data-ttu-id="807a4-118">描述</span><span class="sxs-lookup"><span data-stu-id="807a4-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="807a4-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="807a4-119">0x80041008</span></span> | <span data-ttu-id="807a4-120">參數無效。</span><span class="sxs-lookup"><span data-stu-id="807a4-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="807a4-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="807a4-121">0x80041005</span></span> | <span data-ttu-id="807a4-122">發生型別不符。</span><span class="sxs-lookup"><span data-stu-id="807a4-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="807a4-123">0</span><span class="sxs-lookup"><span data-stu-id="807a4-123">0</span></span> | <span data-ttu-id="807a4-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="807a4-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="807a4-125">備註</span><span class="sxs-lookup"><span data-stu-id="807a4-125">Remarks</span></span>

<span data-ttu-id="807a4-126">此函數會包裝對 [IWbemClassObject：： WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="807a4-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="807a4-127">您可以使用此函數來設定字串和所有其他非 `DWORD` 或非 `QWORD` 資料。</span><span class="sxs-lookup"><span data-stu-id="807a4-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="807a4-128">若為非字串屬性值， `lNumBytes` 必須是指定之屬性類型的正確資料大小。</span><span class="sxs-lookup"><span data-stu-id="807a4-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="807a4-129">若為字串屬性值， `lNumBytes` 必須是指定之字串的長度（以位元組為單位），而且字串本身必須是偶數長度（以位元組為單位），並以 null 終止字元為開頭。</span><span class="sxs-lookup"><span data-stu-id="807a4-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="807a4-130">需求</span><span class="sxs-lookup"><span data-stu-id="807a4-130">Requirements</span></span>  

<span data-ttu-id="807a4-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="807a4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="807a4-132">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="807a4-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="807a4-133">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="807a4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807a4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="807a4-134">See also</span></span>

- [<span data-ttu-id="807a4-135">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="807a4-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
